---
layout: post
title: "Tekk-Fungi: DynamoDB implementation, variant 2"
author: Jacob
tags:
  - draft
---

<h5>Implementing Java CRUD Operations on DynamoDB</h5>Implementing Java CRUD on DynamoDB
While working on my Tekk-Fungi ecosystem, the next natural step involved integrating DynamoDB as a core component of our architecture. Reflecting on my journey so far, I realized how similar this project feels to past endeavors—like my experience in carpentry during the apartment renovation. Both require a solid understanding of the tools and materials, and there’s a learning curve to mastering each.

For the Tekk-Fungi ecosystem, implementing CRUD (Create, Read, Update, Delete) operations on DynamoDB with Java has been an insightful challenge. This marks a significant step towards building a resilient, cloud-ready infrastructure, all while utilizing the dynamic capabilities of AWS’s NoSQL database.

Setting Up the Basics
The project kicked off with setting up DynamoDB locally, ensuring I had a solid environment to develop and test CRUD operations. Maven provided the necessary dependencies, making it easy to install DynamoDB Local and integrate it into my Java application.

DynamoDB Local: Simulates the AWS DynamoDB service, allowing for offline development.
AWS SDK for Java: Powers the interaction between the Java application and the DynamoDB instance.
While it felt like a technical deep dive at first, the initial hurdles reminded me of how far I’ve come in cloud technologies, adding to my broader understanding of the backend ecosystem.

Java CRUD Operations in Action
Once the setup was complete, I began implementing the CRUD operations. My goal was to build the foundations that would later allow me to scale the system and integrate it with other Tekk-Fungi components.

Create: Writing new items into DynamoDB using Java involved mapping objects into the correct format for storage. This required understanding how partition keys work— a new concept compared to traditional relational databases.

Read: Retrieving data is straightforward using partition and sort keys, although scanning large tables can get inefficient. Understanding how to optimize read operations for performance was a great learning experience.

Update: This part was trickier than expected since DynamoDB doesn't support traditional updates in the same way relational databases do. Instead, it overwrites existing records. It took some planning to ensure no data was inadvertently lost.

Delete: Finally, removing items was easy once the partition key was well understood, though, much like my carpentry work, I had to be cautious of unintended side effects.

Lessons Learned
The deeper I dive into DynamoDB, the more I appreciate its unique approach to data management. One unexpected challenge was adapting to its NoSQL structure, particularly with partition and sort keys. Much like getting the layout right in carpentry, ensuring the structure of my DynamoDB tables aligned with the access patterns took some rethinking.

Balancing technical work with personal life, particularly with the newborn at home, has been a challenge. But, just like each milestone in the renovation project, this experience has taught me the value of patience and steady progress. Mastering this technology doesn't happen overnight, but with each passing day, I'm seeing the pieces come together—just like those long nights figuring out how to level the floor.

Looking Ahead
There’s still a lot of ground to cover in this DynamoDB journey. Next, I’ll dive into pagination and batch actions to handle larger datasets more efficiently. The lessons learned here will not only be crucial for the Tekk-Fungi ecosystem but will also sharpen my backend development skills with cloud architectures. I’m also looking forward to exploring advanced indexing techniques to improve query performance and scalability.

While DynamoDB has certainly been an adventure, I see this as just the beginning of its integration into my projects.


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