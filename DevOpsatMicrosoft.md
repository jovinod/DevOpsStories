>![Note] This document is based on the learnings of few members of the Azure DevOps team, based on their journey of adopting these practices within their group

# How do you apply DevOps for developing the Azure DevOps services?
Azure DevOps is built using Azure DevOps, we use our product, rather 95% of Microsoft products use Azure DevOps to code, build, test and deploy.

Let's start from the beginning
* Plan: We follow agile planning and ship every three weeks with hotfixes delivered every day. Few of our microservices also ship every week. The teams are driven by team autonomy i.e. what and how they deliver but guided by enterprise alignment on uber goals. 
* Code: One code base across the whole product, single master branch for all 600+ of us. The pull-request workflow combines both code review and the policy gates. 
* Build and Test: Multiple builds a day and with every PR build we run 85K unit tests to ensure master is always green. In our CI builds we do integration and end to end tests to ensure code can be shipped everyday. So we test continuously and reliabily. 
* Deploy: We have automated deployments and ship every 3 weeks with hotfixes delivered everyday. We also follow progressive disclosure i.e. ship first to ourselves for dogfooding, then to our early adopters, and then to increasingly larger circles of customers with continuous monitoring of performance, error and usage. This ensures that there is no issue at scale as well as helps us fear feedback early on and react faster. Evidence is gathered in production. 
* Measure: We follow build, measure and learn principle and this is incorporated in everything we do from planning to delivery to customers.

# What are the main learnings from your DevOps journey?
We have been on this journey for a decade now and we aren't done yet. However at various stages through this journey we have had numerous learnings. While it's difficult to list all of them here, we have listed a few that were critical to our success. 

## Break Long Cycles 
 When Azure DevOps started on this journey we use to ship services as part of multi-year release cycles. Our first step was to move to a 3 weeks sprint. Yes!!! from multi-year to 3 weeks. But why 3 weeks? Well, based on experimentation 2 weeks felt too short and 4 too long. Was that a smooth ride? Absolutely NOT!!! We executed shorter waterfall in these 3 weeks for a long period. We had separate stabalization sprints and above all huge technical debt. However had we not taken this first step, we wouldn't have encountered these second tier issues.

## Alignment & Autonomy
With nearly 40 feature crews working across the globe, we realized soon the need for Team Autonomy and Alignment. Autonomy is the freedom that each feature crew enjoys defining its own goals to maximize the customer impact, while Alignment is the alignment of crew's goals with the team's and organization’s objectives. Think of it as the glue between the operations and strategy that acts as the guiding light of each member of the team. Let's look at an example

A feature crew owns its own backlog. It decides what will be shipped in the next few sprints. It decides the backlog based on the conversations that each team is having with its customers and partners. This is team autonomy.

While at the same time, all feature crews within a product are aligned to speak the same taxonomy in the organization e.g. Sprints for each teams stars and ends on a fixed date.

## Ownership
At the start we had thousands of tests.  They were written by “testers” to test code written by “developers”.  While there were some advantages of this model – like clearly measurable and controllable investment in test, expertise and career growth in the testing discipline, etc. there were also many disadvantages – lack of accountability on the developers, slow feedback cycle (introduce bug, find bug, fix bug), developers had little motivation to make their code “testable”, divergence between code architecture and test architecture made refactoring and pivoting very hard/expensive, and more.

We combined the dev and test orgs into a consolidating “engineering” org.  For the most part, we eliminated the distinction between people who code and people who test.  That’s not to say every person does an identical amount of each, but every person does some of everything and is accountable for the quality of what they produce.

## Shift Left Quality
As mentioned above, we had thousands of tests. A very high percentage of our tests were end-to-end functional “integration tests”.  Often they automated UI or command line interfaces.  This meant that they were very fragile to small/cosmetic changes and were very slow to run.The result of all of this is that full testing would take the better part of a day to run, many more hours to “analyze the results” to identify false failures and days or weeks to repair all the tests that were broken due to some legitimate change the in the product. So, few years ago, we started on a path to completely redo testing. We now run almost 80K+ unit tests in every pull request. We still do integration testing, however shifting the quality left with unit tests has helped us get the feedback much early in the cycle as well as reduce the size of our integration tests significantly. You can read  more on [how we approach testing...](https://devblogs.microsoft.com/bharry/testing-in-a-cloud-delivery-cadence/)

## Feature Flags
Our organizational goals are pivoted heavily on customer centricity which pushed us to adopt progressive disclosure of features, enabling continuous delivery of value to our customer and receiving feedback early in the cycle. This was achieved using **Feature flags**. Feature flags support a customer-first DevOps mindset, to enable (expose) and disable (hide) features in a solution, even before they are complete and ready for release. We rely heavily on them for any new feature additions or major changes to an existing one. Combined with the Ring based deployment, it has helped us tremendously to gain the confidence in releasing a change. You can read more about [feature falgs...](https://docs.microsoft.com/en-us/azure/devops/migrate/phase-features-with-feature-flags?view=azure-devops)

## Ring Based Deployments
With a varied set of customers that included individual contributors (e.g. MVPs), small teams (as small as 5 members) as well as large enterprises, **Deployment rings** helped us adopt the production-first DevOps mindset and limit the impact on end users, while gradually deploying and validating changes in production. Impact (also called blast radius), is evaluated through observation, testing, analysis of telemetry, and user feedback. Starting with the innermost ring we have **Canaries** who voluntarily test bleeding edge features as soon as they are available, followed by **Early Adoptors** who voluntarily preview releases, considered more refined than the canary bits and finally the **Users** who consume the products, after passing through canaries and early adopters. Our **Early Adoptors** also includes all the teams in Microsoft building different products using Azure Devops. You can read more about [Ring based deployments](https://docs.microsoft.com/en-us/azure/devops/migrate/phase-rollout-with-rings?view=azure-devops)


# What benefits has DevOps brought for the Azure DevOps team at Microsoft?
If I look back, DevOps has fundamentally changed how we operate in Microsoft. We have come a long way from where we started almost 9 years back but in this entre journey we were always trying to solve a small problem or eliminate a small wastage. Each of these investments translated into growth of people, streamlined processes, and creating great products to ship customer value. Some benefits worth a mention are:  
  
- Better team purpose: Each developer in Microsoft is driven by tremendous purpose with the intent to make a deep impact in our customer's life. One of the main reasons for such highly motivated teams is the culture, that is geared towards creating clarity, shipping success, and learning from mistakes.  

- Ship faster while optimizing for learning: As I mentioned above, learning from mistakes is easier said than done. We don't ship features and then learn as they fail. We ship experiments that are geared around learning and as we learn we are able to pivot or persevere whether our hypothesis is validated. All of this is only feasible because the system is geared towards shipping an experiment fast,  learn from it as soon as possible, and course correct and redeploy. We have come a long way from shipping thrice a year to shipping thrice a day and this change is the way we deliver value to our customers is because now we have the ability to continously deliver value.

- Running the business on metrics: It is often said that you build what you measure. We use lead and lag indicators that help us measure product usage, velocity, and live site health. In the journey we have also identified metrics that could be regressive in nature. In the process, we have been able to develop an organization that is able to make much more informed data drivern decisions. Product Managers make feature decisions based on usage data form users. Engineers are able to identify and root cause issues even before the first customer reports a bug. Are people using a feature? Are they happy with it? are not subjective conversations but measurable facts. 

- Live site culture and reliable site engineering: We weren’t good at running services instead of shipping products. We had to build a new muscle with service reliability engineering. Now the end to end process from the moment a live site incident happens the team has developed expertise in mitigation, root causing, monitoring and baking those learnings back into the product. An important learning has also been being transparent about our mistakes and sharing our learnings so that other organizations managing services can learn from our mistakes. 

Having a team purpose, shipping faster, measuring what we ship, and ensuring service availability translates into customer value and empowering every organization and individual on the planet to achieve more - which also happens to be our vision statement.
