---
layout: post
title: "Cucumber and BDD tinkering"
author: Jacob
---
<h5>A glance at BDD, my Cucumber adventure</h5>
Quickly after joining my team, I learned about the Javascript testbot that works but somebody left to slowly be forgotten.
Once granted time, the team looked into refactor the artifact using Cucumber as the new default tool to conduct and run automated integration testing with.

<br/>
<div style="text-align: center"><img class="medium-img" title="cucumbers" alt="cucumbers" src="/assets/posts/cucumber-and-bdd/cucumbers.jpg"></div>
<br/>
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
<div style="text-align: center"><img title="tags" alt="tags" src="/assets/posts/cucumber-and-bdd/tags.png"></div>
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
<div style="text-align: center"><img title="scenario-outline" alt="scenario-outline" src="/assets/posts/cucumber-and-bdd/scenario-outline.png"></div>
<br/>
<br/>

>Cucumber test result

<br/>
This is after one _"Security Access Control"_ execution, here is where you can revisit all tests cases and find out their result, execution time, errors and report information.

<br/>
<div style="text-align: center"><img title="test-results" alt="test-results" src="/assets/posts/cucumber-and-bdd/test-results.png"></div>
<br/>
<br/>

**What I like about Cucumber**

- Run quick and scheduled automatic testing suites
- Generate reports based on tested features and system behavior
- Easily prepare systems and data for load test
- Conduct initial troubleshooting without programming knowledge

<br/>
Before leaving the team, one of my senior colleagues left me with a great gift and idea. 
Prior to decommissioning the old testbot, we used it for load testing but we had to keep track of a various tools, execute python scripts in sequence to update required data and align system processes. 

With Cucumber we can instead utilize Scenarios and Steps to easily prepare and configure the system from one place. 
Since our system is scheduled for load testing once every Program Increment, implementing a _"one-click load test preparation"_ will be my next endeavor.

<br/>

_If you have any great ideas on how to use Cucumber, feel free to contact me - **I'd love to learn more!**_

---
Cucumber Documentation - <a href="https://cucumber.io/docs/cucumber/" class="static-link">Docs Homepage</a>
<br/>
Cucumber Anti-Patterns - <a href="https://www.thinkcode.se/blog/2016/06/22/cucumber-antipatterns" class="static-link">Think Code Blogpost</a>
<br/>
<br/>
Feel free to browse more posts from other <a href="https://www.squeed.com/vilka-vi-aer/squeeders/" class="static-link">Squeeders</a> in our - <a href="https://www.squeed.com/julkalender-2023/" class="static-link">Christmas Calendar 2023</a>

<br/>
<div style="text-align: center"><img class="small-img" title="general-tech-picture" alt="general-tech-picture" src="/assets/posts/cucumber-and-bdd/general-tech-picture.png"></div>
<br/>

---

## Todo's
The current main goal is to take care of our newborn - we are still trying to find our routines every day.

Call to papers has been announced for our upcoming internal conference <a href="https://squeedbrew-tech-2025.sessionize.com/" class="static-link">SqueedBrew Tech 2025</a>.
<br/>
This year's talk was a mix of topics of which I've stumbled upon last two years <a href="https://squeedbrew-tech-2024.sessionize.com/" class="static-link">SqueedBrew Tech 2024</a>.

Here are the latest updates from my backlog, detailing stories and their status at the moment.

#### Hobby projects
[ - ] Plan for future journal entries - In progress, I have amassed a lot of interesting topics - time to do work!
<br/>
[ - ] Finish Tekk-Fungi-Feed component - In progress, major rewrite of learning journal with Minima V3.
<br/>
[ - ] Revisit Tekk-Mycelium-Maestro - In progress, glanced att implementing a WAF, more work than planned.
<br/>
[ x ] Refactored GitHub Pages - Done, there are always more stuff I can add but at least now we have a starting point.

#### Activities
[ x ] Visited "Botaniska Trädgården" - Done, I have been longing to visit since we moved here, I miss Gardening!
<br/>
[ - ] Started going out more - In progress, our daughter is growing, and we cautiously introduces more public spaces.


####  Food
[ x ] Made another pizza dough - Done, tried another oven setting and crust got crispier, overall better.
<br/>
[ x ] Surprise my fiancé with a "Kräftskiva" - Done, it was great, but we overdid it in terms amount of food.

#### Reading
[ - ] Finish L'Abbé C by Georges Bataille - Paused, still no progress, reading AWS Well-Architected Framework instead.
<br/>
[ x ] Push forward AWS Developer exam to October - Done, since it is on discount, I will take Solutions Architect as well.
<br/>
[ - ] Schedule AWS Solutions Architect exam in November - In Progress, worth a try since the exams have some overlap.
<br/>
[ x ] Read chapter in "Modern Software Engineering" - Done, I chose chapter 4, "Working Iteratively", will discuss in entry.

#### Training
[ - ] Running, Gym, Yoga, Bouldering - Paused, trouble getting out, I aim to at least get a 10-minute walk after each meal.


---
Thank you for your time, follow as I continue to explore and document my journey.

Take care!