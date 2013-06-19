---
published: false
layout: post
title: The Dark Matter of Public Policy Data (Part 1)
author: Nick Mader and Rob Mitchum
pic: "dark-matter.jpg"
---

Imagine you are asked to compare patient outcomes at area hospitals. In minutes, you can pull the [Medicare data](https://data.medicare.gov/) for 30-day mortality rates after a heart attack, heart failure or pneumonia, and start crunching numbers. 

But say Hospital A is in a low-income neighborhood with high rates of diabetes, cardiovascular disease and other chronic conditions. Hospital B is in an affluent suburb where patients have access to healthy food and walkable streets. Hospital C serves a diverse population, but has a world-famous cardiologist on staff that specializes in caring for complex patients with poor prognoses. 

Simply finding the average mortality rates for each hospital - without taking all this context into account - would leave you with the incorrect conclusion that Hospital B is best for patients and Hospital C or A is the worst. 

So how can you more accurately compare each hospital’s quality of care, or the skill of their doctors? What can the data tell you -- and what does it miss? 

#### The Illusion of Data

Health care organizations and other entities that receive federal or state dollars are increasingly required to demonstrate their effectiveness to continue receiving funds. Both policymakers and the organizations themselves are motivated to scale up what’s working and leave behind what isn't. 

But how can data science create meaningful evaluation of social programs while avoiding the pitfalls of false comparisons and misleading correlations that factor into high-stakes decision-making?

Some of the Data Science for Social Good projects will need to grapple with this question as they evaluate programs designed to help at-risk school children and first-time mothers. Many factors influence a student’s academic performance or a family’s health – not all of which are reflected in the data that the program collects. 

For example, as the [Chicago Teacher’s Union has argued](http://www.ctunet.com/media/press-releases/ctu-position-paper-cites-damaging-inadequacies-and-misconceptions-in-high-stakes-testing), a student's standardized test scores may not include adequate information about a difficult home situation, violent conditions on their route to school, or psychological problems that influence learning.

Because of this missing data, statistical methods can produce misleading answers that sound more rigorous and concrete than they are in reality. 

The consequences of this illusion can have severe consequences. 

An effective program that targets kids who are at-risk in ways we can't account for may look ineffective, leaving the program vulnerable to loss of funding or complete shutdown.

#### How To See Invisible Data

To avoid these mistakes, we’re training Data Science for Social Good fellows to worry about what the data doesn't show. They are asked to consider how they can combine the insight of data with on-the-ground expertise in their projects. 

This week and next, the fellows are meeting with their partner organizations – either at our downtown space, or, ideally, out in the field – so partners can communicate their needs, priorities and concerns. These interactions are meant to help the fellows understand the data the partners are sharing, but also the significant information that’s missing. 

Drawing from the partners’ expertise in their fields will make our program evaluations more accurate, useful, and considerate of the high stakes involved for these programs and the individuals they serve. By recognizing the gap between the numbers and the real world, the fellows can build the appropriate caveats into their conclusions.

There are also statistical methods for detecting these "dark matter" factors and adjusting the quantitative conclusions accordingly. Econometrics, which often deals with similar data analysis problems, has developed tools including instrumental variable and control function methods to filter out the hidden influence of unobserved factors and reach a more accurate conclusion about an intervention's effectiveness.

An instrumental variable is associated with how a treatment is chosen, but is not associated with factors that play into successful outcomes, allowing a researcher to separate how individuals wind up receiving treatment from studying how they do after receiving it. A control function approach uses instrumental variables to account for what is not observed as a function of what we do observe. 

In our hospital example, patients who travel farther for treatment might be predicted to have more severe disease in general than those who go to the nearest clinic. Even without data on the severity of the cases each hospital receives, these methods can be used to estimate this factor's impact.

The goal is to improve care in the city by learning what works and spreading those ideas, rather than just rewarding the good and abandoning the bad. Finding the most accurate path to that goal is as much about understanding the data that’s missing as it is about analyzing the data that’s there.

In the next two parts, we’ll go more in-depth on some of the statistical methods used to address this problem, and follow the fellows as they visit one of our project partners and chat with workers on the front line of their organization.

*Nick Mader is an economist at [Chapin Hall](http://www.chapinhall.org/) and a Data Science for Social Good mentor. Rob Mitchum is a science writer for the [Computation Institute](http://ci.uchicago.edu).*
