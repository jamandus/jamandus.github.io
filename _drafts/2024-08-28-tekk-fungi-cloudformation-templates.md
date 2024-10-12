---
layout: post
title: "Tekk-Fungi: CloudFormation templates"
author: Jacob
tags:
  - draft
---
**A glance at BDD, my Cucumber adventure**
<br/>
Refactoring an old Javascript testbot, then Cucumber and Gherkin enters!

<br/>
<div style="text-align: center"><img title="cucumbers" alt="cucumbers" src="/assets/posts/cucumber-and-bdd/cucumbers.jpg"></div>
<br/>

Quickly after joining my team, I learned about the Javascript testbot that works but somebody left to slowly be forgotten.
Once granted time, the team looked into using Cucumber as the new default tool to conduct and run integration testing with.

**How can you use Cucumber?**

Cucumber is a testing tool that supports behavior-driven development(_BDD_), enabling users to define and run automated tests based on Gherkin syntax. **What is Gherkin you might wonder?**
<br/>
It is a language which aim to describe the behavior of code in a way that is easy to understand(_plain text_) without the requirement of technical knowledge.
My team uses Java but Cucumber can be used with various other programming languages, like Ruby or Javascript.

<br/>

>Tags

<br/>
In Cucumber you can use _@Tags_ to enable automated testing, associate certain scenarios and features which then can acts as triggers in scheduled test suites or during deployment processes. 
We use them both as execution triggers and configuration setup in conjunction with the _"Before"_ and _"After"_ step hooks.

<br/>
<div style="text-align: center"><img title="cucumbers" alt="cucumbers" src="/assets/posts/cucumber-and-bdd/tags.png"></div>
<br/>

This picture show both types of tags, _@VehicleApp_ trigger the feature during the components build step and _@SqueedHourly_ is a scheduled testing suite which runs every hour.
<br/>
The _@Vehicle_GDPR_Report_, and _@European_Brand_ ones serves as identification for which configuration will take precedence during the given scenario.
This allows you to easily reuse your step definitions and prevent step files from being bloated.

<br/>

>Background

<br/>
Before both the scenarios in this feature you find a _"Background"_-paragraph. These are a great way to gather step definitions which are shared and they will run before every scenario since they are used by more than one.

<br/>

>Anti Patterns

<br/>
**Try to refrain from creating these patterns**

- Feature coupled or feature specific step definitions, they will cause code duplication
- Conjunction steps, there is a reason they created _"And"_ or _"But"_. Can you find my blunder?
- No clear separation between _"Given"_, _"When"_, _"Then"_, describe the context, the action, and the outcome.

<br/>

>Scenario Outline

<br/>
This particular feature runs API security checks on a longer interval based on the _@SqueedDaily_ tag. This Scenario will run the same test case with different values. 
<br/>
If you have worked with Java and JUnit 5 you might recognize the similarities to the _"Parameterized Tests"_, it is a great way to dynamically feed test data to a single test case.

<br/>
<div style="text-align: center"><img title="cucumbers" alt="cucumbers" src="/assets/posts/cucumber-and-bdd/scenario-outline.png"></div>
<br/>
<br/>

>Cucumber test result

<br/>
This is after one _"Security Access Control"_ execution, here is where you can revisit all tests cases and find out their result, execution time, errors and report information.

<br/>
<div style="text-align: center"><img title="cucumbers" alt="cucumbers" src="/assets/posts/cucumber-and-bdd/test-results.png"></div>
<br/>
<br/>

**What I like about Cucumber**

- Run quick and scheduled automatic testing suites
- Generate reports based on tested features and system behavior
- Easily prepare systems and data for load test
- Conduct initial troubleshooting without programming knowledge

<br/>
<br/>
Before leaving the team, one of my senior colleagues left me with a great gift and idea. 
Prior to decommissioning the old testbot, we used it for load testing but we had to keep track of a various tools, execute python scripts in sequence to update required data and align system processes. 

With Cucumber we can instead utilize Scenarios and Steps to easily prepare and configure the system from one place.
Since our system is scheduled for load testing once every Program Increment, implementing a _"one-click load test preparation"_ will be my next endeavor.

<br/>

_If you have any great ideas on how to use Cucumber, feel free to contact me - **I'd love to learn more!**_

---

Cucumber Documentation - [Docs Homepage](https://cucumber.io/docs/cucumber/)

Cucumber Anti-Patterns - [Think Code Blogpost](https://www.thinkcode.se/blog/2016/06/22/cucumber-antipatterns)

Feel free to browse more of posts from other [Squeeders](https://www.squeed.com/vilka-vi-aer/squeeders/) in our - [Christmas Calendar 2023](https://www.squeed.com/julkalender-2023/)

<br/>
<div style="text-align: center"><img title="cucumbers" alt="cucumbers" src="/assets/posts/cucumber-and-bdd/general-tech-picture.png"></div>
<br/>

---

## Todo's
The current main goal is to take care of our newborn - we are still trying to find our routines every day.

Call to papers has been announced for our upcoming internal conference [SqueedBrew Tech 2025](https://squeedbrew-tech-2025.sessionize.com/).
<br/>
This years talk was a mix of topics of which I've stumbled upon last two years [SqueedBrew Tech 2024](https://squeedbrew-tech-2024.sessionize.com/).

Here are the latest updates from my backlog, detailing stories and their status at the moment.

#### Hobby projects
[ x ] Add any theme supported by GitHub - Done, I went with Minima v3 but it needs a color overhaul.
<br/>
[ x ] Added old Christmas blogpost - Done, reminded me to find a topic for this years calendar.
<br/>
[ x ] Add second old Christmas blogpost - Done, topic was interesting to revisit, found improvements.
<br/>
[ - ] Finish Tekk-Fungi-Feed component - Paused, I got distracted, had a blast with DynamoDB.
<br/>
[ x ] Finish Tekk-Mushroom-Manor CRUD - Done, next repository task is Pagination and Batch actions.
<br/>
[ x ] Start writing Java for Tekk-Fungi components - Done, next is SQS and SNS implementations.

####  Food
[ x ] Practice making pizza dough - Done, tried two different 12, 24 and 48 hour doughs!
<br/>
[ x ] Practice making tortilla dough - Done, tried 50% corn and 50% wheat, fiancé was no fan of corn.
<br/>
[ - ] Surprise my fiancé with a "Kräftskiva" - In Progress, will host while my parents are visiting in w35.

#### Reading
[ - ] Finish L'Abbé C by Georges Bataille - Paused, I don't have energy at night, gonna try WC reading.
<br/>
[ x ] Take AWS Developer/Solutions Architect practice exams - Done, 45% and 50% is a good start.
<br/>
[ - ] Push forward AWS Developer exam in September - In Progress, not sure when I will find time.
<br/>
[ - ] Read chapter 1 in "Modern Software Engineering"- In Progress, will implement learnings in Tekk.

#### Training
[ - ] Running, Gym, Yoga, Bouldering - Paused, low energy and still isolated, focus on routines.

---
Thank you for your time, follow as I continue to explore and document my journey.

Take care!