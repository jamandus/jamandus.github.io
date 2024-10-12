---
layout: post
title: "Tekk-Fungi: DynamoDB implementation, variant 1"
author: Jacob
tags:
   - draft
---
<h5>Implementing Java CRUD Operations on DynamoDB</h5>
When I first considered writing about Java and DynamoDB, I couldn’t help but compare it to my apartment renovation project in Stockholm. Like carpentry, tackling DynamoDB required me to learn a new set of skills—both practical and theoretical. While one involved wood, the other involved database tables and code, but the challenges of learning something unfamiliar remain universal.

I’ve noticed that diving into new technologies, whether it's home improvement or database design, offers the same combination of excitement and hesitation. Setting up CRUD (Create, Read, Update, Delete) operations on DynamoDB in Java is another milestone in my cloud development journey, but, like every project, it brings along unexpected detours.

Setting Up DynamoDB CRUD with Java
For this part of my learning journal, I focused on creating a Java application that performs basic operations on DynamoDB. My motivation behind this is twofold: first, I want to expand the functionality of my ongoing Tekk-Fungi ecosystem, and second, it's a necessary skill to master for any backend developer working with AWS technologies.

1. Create
   Starting with adding new items to the DynamoDB table. Using the AWS SDK for Java, I wrote simple methods that push new records to the database. My primary challenge? Mapping Java objects into DynamoDB's item format. Once I understood the annotations required for my model classes, it all clicked into place.

2. Read
   This step was about retrieving data—querying specific items by their partition key or scanning the entire table. Scanning felt easy at first, but it's inefficient for larger datasets. Querying based on partition and sort keys proved to be more elegant, and I’m beginning to appreciate DynamoDB’s flexibility in handling data access patterns.

3. Update
   The update functionality posed more of a challenge. Unlike traditional relational databases, DynamoDB doesn't have an "update" command in the conventional sense. Instead, it overwrites the existing item, which forced me to carefully plan my operations. In retrospect, understanding DynamoDB's mechanics around atomic counters and conditional updates added an extra layer of insight into its unique behavior.

4. Delete
   Finally, deleting an item was straightforward once I got the basics down. However, I had to be cautious with partition keys to avoid accidentally deleting more than I intended—an issue I’ve learned to double-check in future operations.

Lessons Learned
Much like my previous analogy of renovating my apartment, working with DynamoDB CRUD operations showed me how planning matters just as much as execution. I initially underestimated how DynamoDB's NoSQL structure differs from traditional relational databases. The concepts of partition keys and sort keys took some getting used to. It reminded me of the time I underestimated how tricky it would be to level an uneven floor—turns out, both in carpentry and coding, it's best not to rush the fundamentals.

More importantly, this exercise forced me to refine my problem-solving approach. Instead of trying to brute-force my way through code, I took a step back and looked at the bigger picture. I spent more time understanding the relationships between tables and indexes, much like I would carefully study the floor plan of an apartment before tearing down walls.

Additionally, balancing technical work and personal life continues to be an ongoing process. Between implementing these CRUD operations and taking care of the newborn, I’ve realized that progress, in both my professional and personal life, comes with patience and persistence.

Looking Ahead
I’m far from done with DynamoDB. My next goal is to introduce pagination and batch actions in the database to improve performance, especially when dealing with large data sets. This will integrate seamlessly with the other Tekk-Fungi components I’ve been working on, taking the ecosystem one step closer to completion.

Also, I’m excited to explore deeper concepts like DynamoDB Streams, which will allow real-time tracking of changes in my tables—an exciting feature for the automation testing I plan to integrate in the future.

As always, a shoutout to Martin for his unyielding support, both with tech and keeping me grounded during these intense learning sprints.

Stay tuned as I continue documenting my progress in this dynamic cloud ecosystem journey.


---

DynamoDB Documentation - <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.html" class="static-link">DynamoDB Setup</a>

DynamoDB Local versions - <a href="https://mvnrepository.com/artifact/com.amazonaws/DynamoDBLocal" class="static-link">Maven Repository</a>

NoSQL Workbench for DynamoDB - <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/workbench.html" class="static-link">Workbench Docs</a>

---

## Todo’s

The current main goal is to take care of our newborn - we are still trying to find our routines every day.

Here are the latest updates from my backlog, detailing stories and their status at the moment.

#### Hobby Projects
[ - ] Finish initial Tekk-Fungi-Feed component - Paused, started something that has been brewing for a while.
<br/>
[ x ] Start Tekk-Spore-Scrutinizer component - Done, autmatic testbot for Tekk-Fungi ecosystem, powered by Spring.
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
[ - ] Running - In Progress, keeping up with a steady routine.
<br/>
[ - ] Gym and Yoga - Blocked, focusing on recovery and flexibility exercises.

---
Thank you for your time, follow as I continue to explore and document my journey.

Take care!