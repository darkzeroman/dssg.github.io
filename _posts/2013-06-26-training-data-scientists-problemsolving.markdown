---
published: true
layout: post
title: "Training Data Scientists: Problem-solving"
author: Juan-Pablo Velez
pic: "aca-ideas.jpg"
---

Data science isn't just about creating algorithms, writing code, or visualizing data. The first step is finding the right problem to solve.

Many of the governments and nonprofit organizations we've talked to are excited about using data to make better decisions. But most aren't quite sure where to start, while others pitch lots of problems that are initially too vague to solve with data.

To help these organizations grow their impact, then, data scientists must be hands on: they need to quickly learn the ins and outs of unfamiliar fields, from health care to energy to municipal government. They need to have a nose for understanding what data is available both inside and outside an organization, and a knack for distilling ill-defined problems into clear and tractable ones.

None of this happens just in front of a computer - it happens by getting out there and talking to people. To learn these problem-solving skills, fellows are working closely with real organizations throughout the summer.

Here's how it's working: they spent the first two weeks of the program talking to our partners in order to understand the social problems they work on, how the organizations function, and what is - [and isn't](/2013/06/19/the-dark-matter-of-public-policy-data.html) - in the data. Next, they're using this context to flesh out their projects, and they'll be checking in with partners every week to make sure projects are heading in the right direction.

#### Problem-solving bootcamp 
Just as we organized a tech bootcamp to acquaint fellows with the [data tools available to them](/2013/06/08/training-data-scientists-tools.html), we put on a problem-solving bootcamp to prep them for these partner meetings. 

Dean Malmgren from [Datascope Analytics](http://datascopeanalytics.com/), a Chicago-based analytics consultancy, gave the fellows a whirlwind introduction to the key steps in [data science problem-solving](http://strata.oreilly.com/2013/04/why-why-why.html): defining the problem and brainstorming a data solution.

Instead of discussing these techniques in the abstract, though, we applied them to a real organization - the State of Illinois.

#### The problem: Insuring people in Illinois

Brian Gorman, George Letavish, and Erik Wallenius (pictured below) from the State of Illinois are some of the key players implementing health care reform in the land of Lincoln. They dropped by the office to tell the fellows about the immense policy challenge they're facing: enrolling hundreds of thousands of Illinois' uninsured people into the State's new [Health Insurance Marketplace](http://www2.illinois.gov/gov/healthcarereform/Pages/HealthInsuranceMarketplace.aspx).

<img src="/img/posts/malmgren-gorman.jpg">
 
As is often the case when data scientists work with a new organization, most fellows knew little about the world of health insurance or the Affordable Care Act. (If that describes you too, click [here](http://www.washingtonpost.com/blogs/wonkblog/wp/2012/06/24/11-facts-about-the-affordable-care-act/) for an excellent primer on the ACA.)
 
So they started from scratch, peppering our partner with questions in order to grasp the essentials of health care reform and pin down the specific policy problem the State is facing. Here's what they found:

An estimated 1.6 million Illinois residents lack health insurance. The Affordable Care Act aims to change this by making most of these folks eligible for affordable health care coverage.

Here's how it'll work: on January 1st, 2014, most Americans will be required to buy health insurance. Those who aren't already covered by their employer will be able to buy coverage from new [online health insurance marketplaces](https://www.healthcare.gov/). Depending on the state, these marketplaces will be run by the federal government, state government, or a partnership between the two.

By encouraging competition between health insurance companies, the marketplaces are supposed to drive down the price of insurance plans, making them more affordable to the millions of people that will suddenly be required to buy them. On top of that, many lower-income people will qualify for subsidies that make coverage cheaper still.

Illinois' marketplace will let individuals and small businesses shop for insurance plans, compare their costs and benefits, and apply for them online.

The challenge: ~80% of the people the State of Illinois wants to insure through the marketplace have never heard of it. So Illinois Governor Pat Quinn has put together a team to get the word out about the program, and to persuade as many uninsured people as possible to sign up.

This marketplace team is mounting an [ambitious marketing campaign](http://www.chicagobusiness.com/article/20130412/NEWS03/130419933/ap-interview-quinn-hire-to-market-health-overhaul) later this year. Their goal: to enroll 486,000 of Illinois' 1.6 million uninsured by the end of 2014. To reach these folks, they'll be able to spend up to $35 million on phone calls, direct mail,, and ads - from TV spots to tweets. But who exactly should they be targeting with all this outreach?

That's the big problem the team is facing: how do you reach hundreds of thousands of uninsured people - many of whom have never had coverage before - and persuade them to buy a product they're required to purchase?

And how do you also convince healthy people to enroll, since they're needed in the insurance pool to keep the plans affordable for everyone?
 
#### Brainstorming solutions
For the marketplace team, the answer lies in using data. Despite having only a few months left to launch their marketing campaign, the team is determined to make it data-driven.

After we had grasped the policy problem, Gorman and his colleagues recast it in data terms: they want to predict which Illinois residents are likely to be uninsured, and use this list to target individual households (initially with door knocks and phone calls).

The inspiration for this approach comes from the 2012 Obama campaign, which built statistical models to predict the likelihood that every known voter would go to the polls and vote for Obama.

To do individual-level prediction, however, you need individual-level data. The Obama campaign had lots of it: in addition to running surveys, they had access to the voter file, a massive publicly available list of all registered voters in the country.

The State of Illinois, on the other hand, has almost no data on individuals. There's no "voter file" for the uninsured - no central list of everyone in Illinois without healthcare coverage. And there are important state and federal privacy laws preventing the team from tapping into unemployment insurance rolls, patient medical records, and other key individual-level datasets that could point them to uninsured folks.
 
With that constraint in mind, the fellows split off into smaller groups to brainstorm analytics solutions to the State's targeting problem. 

<img src="/img/posts/aca-group.jpg">

After an hour of brainstorming, we distilled themes from the dozens of proposed solutions. Three approaches to the targeting problem emerged:

- Start simple, get smarter over time: The team could start with publicly-available neighborhood demographic data from the Census Bureau. Though not individual-level, they'd use this data to create a rough statistical model and target their outreach to places with high rates of uninsured people. They'd use every interaction with uninsured folks to gather individual-level data about them, and use it to improve the targeting model.
 
- Find people where they are: Alternatively, the State could target churches, libraries, veteran's groups, schools, and other existing hubs that serve uninsured people and have deep networks in local communities. Many of these hubs could be located using open data from governments or web services like Yelp and Google maps.

- Use people’s social networks: Since people tend to know people like themselves, the State could incentivize the newly-enrolled to evangelize the marketplace to other uninsured folks in their social networks, online or off. For example, people could refer their friends and family to the marketplace on Facebook, and the State could experiment with different messages to find which ones resonate with different demographics and lead them to sign up.

<img src="/img/posts/nick-aca-ideas.jpg">

Of course, the workshop was an informal opportunity for the fellows to sharpen their problem-solving skills, and for the State to pick the brains of three dozen data scientists as they develop their analytics strategy and not to solve the problem in that one session.

Some of these off-the-cuff ideas would be tough to implement on the State's aggressive timeline, others might turn out to be ineffective or unworkable. It’s important for data scientists to think creatively but still be aware of the practical constraints.

It's all too easy for data scientists to get excited by a fresh dataset and generate dozens of interesting questions about it. Unless they put in the hours up front to understand the partner's work and needs, the risk is that most of these questions won't be relevant or actionable for them.

