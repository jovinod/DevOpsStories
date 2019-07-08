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
I would say the first and key one is DevOps is a journey, you are never done and can keep improving to deliver value to your customer. Secondly, culture plays a key part, the culture of growth mindset, the culture of experiment and this learning is key in making your DevOps journey successful. It is a transformation from celebrating success to celebrating failure and learning from those mistakes and course correct to add value to customers.

# What benefits has DevOps brought for the Azure team at Microsoft?
If I look back, DevOps has fundamentally changed how we operate and the benefits are immense. To name a few
Better team and organisation alignment
Ship faster and continuously deliver value to customer
Backlog groomed with learning
Running the Business on Metrics
Measuring every improvement whether its new feature or performance improvements
Live site culture and reliable site engineering

