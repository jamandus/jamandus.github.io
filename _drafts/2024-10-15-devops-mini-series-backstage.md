---
layout: post
title: "DevOps Mini Series: Backstage"
author: Jacob
tags:
  - draft
---
<h5>Local DynamoDB setup with Maven</h5>
<br/>
This DynamoDB adventure has been long-coming, I was exposed to its kit on an assignment a while back and I really enjoyed it. 
It was my first experience with a NoSQL database, on top of that they were also running a local instance of the cloud provided service.
In contrast to my apartment renovation, this is a great way of being able to develop, test, and **learn while doing** without actually having to put down any _"training-money"_.

This entry focuses on the process of how I got my local instance up and testable, rather than diving deep into my specific table design or exploring index strategies.
To be frank, I haven't iterated or challenged my first database schema once at the point of writing.

Already out of scope, diving right into the technical part of DynamoDB setup.

There are two additional ways of using DynamoDB local, either you simply download the archive or run it as Docker image. 
We are going to revisit this and run it as a Docker image as well, but at a later stage once the new <a href="https://github.com/jamandus/tekk-spore-scrutinizer" class="static-link">tekk-spore-scrutinizer</a> component has matured past its initial stage.

In my <a href="https://github.com/jamandus/tekk-mushroom-manor" class="static-link">tekk-mushroom-manor</a> I run DynamoDB Local v.2 as a Maven dependency as it was the most natural move for me.

<br/>
>## The Setup Process

<br/>


In short, to get up an running you need to import necessary Maven packages, configure a local server to adhere to your environment such as which port or amount of memory usage. 
And lastly define a DynamoDB client, specifying credentials, http client and endpoints in order to create database resources and configuration for your local instance.

<br/>
>Step 1: Maven dependencies

<br/>
To integrate DynamoDB Local, start by adding necessary Maven dependencies to the project pom.xml, let's dissect and analyze what's going on:
<br/>
<br/>


```
<dependency>
    <groupId>software.amazon.awssdk</groupId>
    <artifactId>dynamodb</artifactId>
    <version>2.27.7</version>
</dependency>

<dependency>
    <groupId>software.amazon.awssdk</groupId>
    <artifactId>url-connection-client</artifactId>
    <version>2.27.7</version>
</dependency>

<dependency>
    <groupId>com.amazonaws</groupId>
    <artifactId>DynamoDBLocal</artifactId>
    <version>2.2.1</version>
    <scope>test</scope>
    <exclusions>
      <exclusion>
        <groupId>software.amazon.ion</groupId>
        <artifactId>ion-java</artifactId>
      </exclusion>
    </exclusions>
</dependency>
```
<br/>
- _dynamodb_: dependency that holds the client classes, used for communicating with Amazon DynamoDB Service.

- _url-connection-client_: used by the AWS SDK to effectively communicate to the Local DynamoDB via HTTP endpoints.

- _DynamoDBLocal_: dependency for the in-memory server instance that mimics the DynamoDB cloud service.

- _ion-java_: excluded since there is a vulnerability within the ion-java package which hasn't been patched yet.
  - CVE-2024-21634 vulnerability is handled by overwriting the infected version to v.1.11.9, a later one without.

<br/>
>Step 2: Configure Local DynamoDB

<br/>
Configuration involves setting up the local server and client. For the server, we specify options like port and in-memory operation.

<br/>
```
public DynamoDB(final String tableName) {
    try {
      LOGGER.debug("Initializing DynamoDB server...");
      initializeServer();
      configureDynamoDbClient();
      createDatabaseSchemas(singletonList(tableName));
    } catch (Exception e) {
      LOGGER.error("Unable to start DynamoDB Test Server", e);
      throw new DynamoDbException(e);
    }
}
```
<br/>
I started configuring by defining host, port and system properties for the server. 
There are a few additional settings available which allow you to somewhat expand and enhance you local DynamoDB experience, but I opted for the most simple ones.

<br/>
```
private void initializeServer() throws ParseException {
    this.server = ServerRunner
        .createServerFromCommandLineArgs(new String[]{"-inMemory", "-port", PORT, "-sharedDb"});
}
```

<br/>
- _-inMemory_:  DynamoDB runs in memory instead of using a database file. Data is lost upon server termination.

- _-port_: The port number that DynamoDB uses to communicate with your application, it defaults to port 8000.

- _-sharedDb_: DynamoDB uses a single database file instead of separate files for each credential and Region.

- _-cors: Enables support for cross-origin resource sharing for JavaScript, useful when building frontend.

- _-delayTransientStatuses_: Introduces delays for operations to simulate the behavior of a real DynamoDB web service.

- _-optimizeDbBeforeStartup_: Optimizes the underlying database tables before starting your local instance.


<br/>
After that our server knows how to start and stop, we now need to define the actual DynamoDB client responsible for resource creation such as tables, indexes, and in my case also correlates to my CloudFormation template

This project is at a point where we only have created configuration for local development, and that will show in the next part as it vastly is simplified compared to the requirements of the cloud.

Our client wants to know which region it should live in and a way to authenticate, since we are creating a local configuration which is more relaxed, we supply dummy values such as "accessKeyId" and "secretKey".

This is made to simply mock and satisfy the AWS SDK syntax requirements. We also give HTTP information on which endpoint/URI and port it will function.
In contrast, cloud configurations require accurate region settings, valid AWS credentials, and will rely on actual AWS IAM roles to securely interact with DynamoDB.

<h5 style="text-align: center">Creating client</h5>

```
private void configureDynamoDbClient() {
    this.client = DynamoDbClient.builder()
        .credentialsProvider(StaticCredentialsProvider
            .create(AwsBasicCredentials
                .create("accessKeyId", "secretKey")))
        .endpointOverride(URI.create(HOST + ":" + PORT))
        .httpClient(UrlConnectionHttpClient.builder().build())
        .region(Region.of(REGION))
        .build();
}
```
<br/>
Defining a cloud configuration is planned further down the road, as we want to enable switching between a live implementation in the cloud and this local instance in our daily life.
<br/>
<br/>

>Step 3: Create DynamoDB resources

<br/>
At this point with our configuration complete, we can now start defining database resources such as tables, attributes and indexes. 
In my case, my Tekk-Fungi ecosystem only have 1 table at this point, but remains easily extendable.
<br/>
<h5 style="text-align: center">Creating table</h5>

```
private void createTable(String tableName) {
    CreateTableRequest request = CreateTableRequest.builder()
        .tableName(tableName)
        .attributeDefinitions(
            AttributeDefinition.builder()
                .attributeName("pk")
                .attributeType(ScalarAttributeType.S)
                .build(),
            AttributeDefinition.builder()
                .attributeName("name")
                .attributeType(ScalarAttributeType.S)
                .build(),
            AttributeDefinition.builder()
                .attributeName("position")
                .attributeType(ScalarAttributeType.S)
                .build(),
            AttributeDefinition.builder()
                .attributeName("foraged")
                .attributeType(ScalarAttributeType.S)
                .build())
        .keySchema(KeySchemaElement.builder()
            .attributeName("pk")
            .keyType(KeyType.HASH)
            .build())
        .globalSecondaryIndexes(createIndexes())
        .provisionedThroughput(ProvisionedThroughput.builder()
            .readCapacityUnits(5L)
            .writeCapacityUnits(5L)
            .build())
        .build();
    try {
      CreateTableResponse response = this.client.createTable(request);
      waitForTableCreation(this.client.waiter(), tableName);

    } catch (DynamoDbException e) {
      LOGGER.error("Failed to create table", e);
  }
}
```
<h5 style="text-align: center">Creating indexes</h5>

```
private List<GlobalSecondaryIndex> createIndexes() {
    return List.of(GlobalSecondaryIndex.builder()
            .indexName(MUSHROOM_LOCATION_GSI)
            .keySchema(KeySchemaElement.builder()
                    .attributeName("name")
                    .keyType(KeyType.HASH)
                    .build(),
                KeySchemaElement.builder()
                    .attributeName("position")
                    .keyType(KeyType.RANGE)
                    .build())
            .projection(Projection.builder()
                .projectionType(ProjectionType.INCLUDE)
                .nonKeyAttributes("foraged")
                .build())
            .provisionedThroughput(ProvisionedThroughput.builder()
                .readCapacityUnits(5L)
                .writeCapacityUnits(5L)
                .build()).build(),
        GlobalSecondaryIndex.builder()
            .indexName(HARVEST_LOCATION_GSI)
            .keySchema(KeySchemaElement.builder()
                    .attributeName("position")
                    .keyType(KeyType.HASH)
                    .build(),
                KeySchemaElement.builder()
                    .attributeName("foraged")
                    .keyType(KeyType.RANGE)
                    .build())
            .projection(Projection.builder()
                .projectionType(ProjectionType.INCLUDE)
                .nonKeyAttributes("name")
                .build())
            .provisionedThroughput(ProvisionedThroughput.builder()
                .readCapacityUnits(5L)
                .writeCapacityUnits(5L)
                .build())
            .build());
}
```
<br/>

>Lessons Learned

<br/>
At one point I was getting a particular error while constructing the table, I had already defined the table in CloudFormation but now time had come to create the actual DynamoDB table with its indexes.

This syntax error was called **ERROR**, it occurred when I was defining additional indexes in conjunction with certain attributes. 
I found myself searching forums, websites and AWS SDK docs to my best ability, never to find the rule prohibiting me from achieving this.

I had no issue while creating or linting my CloudFormation template, so this was isolated to the AWS SDK. 

Solving the issue made me no smarter, it appeared to be a syntax issue whereas if I populated ".globalSecondaryIndexes(createIndexes())" with a method called "createIndexes()" instead of directly building a list with GlobalSecondaryIndex.builder() I could circumvent the issue.

<br/>

>Looking Ahead

<br/>
Next up in my itinerary is developing the Java implementation, starting with a classic CRUD and then extending functionality into more advanced batch operations, adding pagination ability and conditional expressions.
<br/>

The local DynamoDB setup has paved the way for further development in my Tekk-Fungi project.
In my backlog are plans to utilize this setup in the <a href="https://github.com/jamandus/tekk-spore-scrutinizer" class="static-link">tekk-spore-scrutinizer</a> component, 
and eventually create test suites which serve as integration testing within the ecosystem. This journey is about exploration and challenging my technical ability in order to grow.

---

DynamoDB Documentation - <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.html" class="static-link">Local DynamoDB Setup</a>

Local DynamoDB versions - <a href="https://mvnrepository.com/artifact/com.amazonaws/DynamoDBLocal" class="static-link">Maven Repository</a>

Local DynamoDB settings - <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.UsageNotes.html" class="static-link">Usage Notes</a>

NoSQL Workbench for DynamoDB - <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/workbench.html" class="static-link">Workbench Docs</a>

---

## Todo’s

The current main goal is to take care of our newborn - we are still trying to find our routines every day.

Here are the latest updates from my backlog, detailing stories and their status at the moment.

#### Hobby Projects
[ - ] Finish initial Tekk-Fungi-Feed component - Paused, started something that has been brewing for a while.
<br/>
[ x ] Start Tekk-Spore-Scrutinizer component - Done, automatic testbot for Tekk-Fungi ecosystem, powered by Spring.
<br/>
[ - ] Start implementing pagination and batch actions - In progress, outlining the requirements and approaches.
<br/>
[ - ] Explore advanced DynamoDB features - Upcoming, looking into advanced indexing and performance optimization.

#### Food
[ - ] Practice making a new bread recipe - Done, the results were delightful!
<br/>
[ - ] Prepare a surprise dinner for family - In Progress, planning a special menu for the upcoming weekend.

#### Reading
[ - ] Finish “L’Abbé C” by Georges Bataille - In Progress, aiming to complete it soon.
<br/>
[ - ] Review AWS DynamoDB documentation - Done, valuable insights for upcoming projects.

#### Training
[ - ]   Running - In Progress, keeping up with a steady routine.
<br/>
[ - ] Gym and Yoga - Blocked, focusing on recovery and flexibility exercises.

---
Thank you for your time, follow as I continue to explore and document my journey.

Take care!