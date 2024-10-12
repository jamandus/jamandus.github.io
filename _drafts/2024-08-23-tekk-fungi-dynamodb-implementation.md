---
layout: post
title: "Tekk-Fungi: DynamoDB implementation"
author: Jacob
tags:
  - draft
---
<h5>Setting Up Local DynamoDB with Maven & Java</h5>

Initially, I thought about diving right into the technical aspects of DynamoDB setup, but I realized I should first frame the context a bit. 
Similar to how renovating my Stockholm apartment was an entirely new experience in carpentry and building conservation,
working with DynamoDB locally has been a refreshing dive into new territory for me in the cloud development world.

In the spirit of continuous learning, I wanted to tackle setting up a local DynamoDB environment via Maven and integrate it with a Java application. **Why local?**

It provides a sandbox to tinker and experiment without worrying about AWS costs or connection issues, something that allows me to break things without consequence—an invaluable part of learning.

Setting up DynamoDB locally was not only about understanding the infrastructure but about reflecting on how I learn and solve problems.
Documenting the process here helps solidify the learning for me while (hopefully) offering insight to others who may be walking a similar path.
<br/>
<br/>
>The Setup Process

<br/>
To get started, I decided to go with Maven as a build tool for the Java application. 
Maven’s dependency management felt intuitive, and since most of my projects are cloud-based, using DynamoDB in a local environment was the perfect fit for simulating a cloud-native ecosystem.

Here’s a basic overview of the steps:

- **Maven Dependency**: The first thing I did was add the AWS DynamoDB SDK to my pom.xml file. This is what makes communication with the DynamoDB instance possible from the Java application.

- **Local DynamoDB**: Setting up the local DynamoDB instance was surprisingly straightforward. I used Amazon’s downloadable DynamoDB package and configured it to run on my machine. This local setup simulates the behavior of the AWS-hosted DynamoDB, making it perfect for development and testing.

Integration: Finally, the Java code to connect to DynamoDB. I wrote a basic API that allows me to interact with the local database, performing basic CRUD operations—create, read, update, and delete.
While this step took the most time, it felt like a rewarding milestone in this cloud ecosystem journey.
<br/>
<br/>

>Lessons Learned

<br/>
Just like my first post where I reflected on the unanticipated detours in carpentry, I faced a few unexpected hurdles during this process. For one, 
I underestimated the importance of understanding the underlying mechanics of DynamoDB, such as partition keys, global secondary indexes, and throughput settings. 
Working through these challenges helped me sharpen my understanding of distributed databases.

On the personal side, this journey forced me to balance multiple aspects of my life—family, work, and learning. Just as I mentioned in my first entry, the newborn bubble still takes priority. 
Juggling technical work with parenthood requires more scheduling than I anticipated, but it’s teaching me a lot about patience and progress.
<br/>
<br/>

>Looking Ahead

<br/>
The excitement of setting up DynamoDB locally has opened new doors for the rest of my "Tekk-Fungi" project. The next step will be to integrate this setup with my other components, making it part of the larger ecosystem.
<br/>

Similar to the growth mindset I discussed in my first post, this project is about continuous adaptation—whether it's learning new technology, embracing failures, or fine-tuning ideas.

As always, I want to extend a thank you to those who have helped along the way, both directly and indirectly. A shout-out to Martin, whose humor and directness have helped me stay grounded during these technical deep dives.


---

Cucumber Documentation - [Docs Homepage](https://cucumber.io/docs/cucumber/)

Cucumber Anti-Patterns - [Think Code Blogpost](https://www.thinkcode.se/blog/2016/06/22/cucumber-antipatterns)

Feel free to browse more of posts from other [Squeeders](https://www.squeed.com/vilka-vi-aer/squeeders/) in our - [Christmas Calendar 2023](https://www.squeed.com/julkalender-2023/)

<br/>
<div style="text-align: center"><img title="cucumbers" alt="cucumbers" src="/assets/posts/cucumber-and-bdd/general-tech-picture.png"></div>
<br/>

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