---
layout: post
title: "The Dark Matter of Public Policy Data (Part 2): Statistical Solutions"
author: Nick Mader
pic: "dark_matter.jpg"
---

[Part one](/2013/06/19/the-dark-matter-of-public-policy-data.html) of this series talked about the “dark matter” of public policy data -- the invisible factors not present in a dataset that can distort an evaluation of a program’s effectiveness. In this post, we break down some of the statistical methods the field of econometrics has developed to grapple with this issue.

#### A Hypothetical Problem 

Once again, let’s try to compare quality of care at two hospitals. Hospital A is a rural health clinic that has few resources and handles simple cases, while Hospital B is a world-class hospital with strong resources that treats the most severe cases.

In general, adults go to the nearest hospital for care. But in some cases, patients with especially serious conditions will travel long distances to receive specialize care from a specific hospital -- or even a specific doctor.

As a result, the specialist hospital or doctor ultimately serves a population that is not representative of the sick population at large, and not representative of the population served by other hospitals. At first glance, the health outcomes at this hospital will likely look worse than those from a small rural or suburban clinic treating everyday local cases. But econometric methods can help us separate true outcomes from factors in the data that cause illusory distortion.

#### Finding a Mirror for the Unseen

One way to compare the quality of care at the two hospitals is to pick one medical problem they face - say, heart attacks - and compare their respective survival rates.

But this doesn’t give us an apples-to-apples comparison, because we’re not taking into account the severity of the cases each hospital sees. Heart attack patients might have more and less frequent attacks, more or fewer complicating conditions, or different types of precipitating behaviors that influence their prognosis. 

So if we focus on all patients who have a heart attacks, a small clinic may have better survival rates than a specialized hospital because the specialists attend to cases that are more severe on all these hidden dimensions.

In other words, our program evaluation problem occurs because there is a hidden factor affecting both the selection of treatment - which hospital a patient chooses - and the likely outcome - their likelihood of surviving - that we cannot observe: those with the most severe conditions choose the specialty hospital, but they’re also less likely to survive to begin with.

To determine the true effectiveness of a treatment - a statistics term for the intervention being studied; in this case, the quality of care of each hospital - we need to separate how individuals select treatment from how they do after treatment - how patients select their hospital they from how they do after they go.

Suppose we could find a representative subset of heart attack patients -- a group with similar frequency of heart attacks, complicating conditions, and precipitating behaviors -- who only went to the small clinic, and a similarly representative group who only went to the specialty clinic. These subsets form a more accurate basis for comparing the small clinic and speciality hospital than the survival rates of all heart attack patients, since they represent groups of patients where we’ve been able to solve the problem of biased selection into treatment.

#### A Solution in the Distance

The tool that delivers us these “fair” comparisons is called an instrumental variable. It’s a variable - in this case, something about a patient - that is associated with how treatment is chosen, but not associated with factors that play into successful outcomes. 

So we’re looking for a patient trait that influences which hospital they go to (like the severity of their condition,) but does not make them more likely to have a lower survival rate (unlike severity.)

One common example is distance. Suppose we knew where all heart attack patients lived, and we knew that distance played a significant role in determining which hospital they chose. And suppose that the of heart attacks were not associated with location - that is, that patients living further away from the hospital do not tend to have more severe heart attacks than those nearby, or the other way around.

If this was the case, we might be able to find fully representative subgroups of patients selecting treatment at hospital A vs. hospital B by simply picking patients who live very close to each of the hospitals. (As always, it’s necessary to proceed with a sense of how well assumptions match reality.)

#### The Control Function Approach

While instrumental variables such as distance are almost always necessary to solve treatment selection problems, there are several ways that they can be used. 

One way is called control function approach, which accounts for what is not observed as a function of what we do observe. This is a “detection of dark matter” approach, and the instrumental variable is the tool we use for detection. 

In our hypothetical data set, we have information about whether individuals have had a heart attack, where they live, which treatment they chose, and their survival outcome. The invisible “dark matter” missing from the data is the severity of the heart attack. 

Control function methods reflect our intuition. If we see individuals simultaneously choosing the specialty hospital even though they live much closer to the rural clinic *and* having negative outcomes, we suspect that the specialty hospital is attracting those with hard to observe, severe disease. 

In this case, distance as an instrumental variable helps us detect the quantity. Those who live close to and choose the specialty clinic have a balance of good and bad “dark matter” -- there is likely a mix of mild and severe disease. But as we start to look at speciality clinic patients that live far away from it, chances are there is more bad dark matter than good. Patients who live further away from the clinic but choose it anyway are more likely to have severe disease.

By looking across the outcomes of individuals who seek treatment at the specialty hospital based on how far away they live, control function approaches deliver an estimate of the impact of dark matter on outcomes. Once in hand, these invisible factors can be separated from the true impact of the hospital on patient outcomes.

#### More Than Medicine

These methods are also useful in many other settings where organizations try to address some behavioral, educational, financial or medical issue. Not only do these organizations serve populations that differ in ways that may affect their the outcome we care about - from drug use to graduation rates to personal savings - but those population differences are often hard for outsiders to observe with the data they possess.

To add further complexity, the most ambitious organizations strive to reach the most difficult-to-serve and at-risk populations. An after-school program designed to help struggling students reach graduation may work with kids who have both academic and family issues that influence their ultimate performance. Evaluating the effect of this program will need to statistically account for the effects of the family “dark matter” if their data largely consists of test scores and grades. 

Part of studying data is worrying about the information you *don’t* have, because no dataset -- no matter how large -- tells the entire story alone. Econometric methods offer data scientists tools for finding real effects in imperfect numbers, and offer useful conclusions grounded in reality.

*For more information on these methods, the Wikipedia pages on [instrumental variables](http://en.wikipedia.org/wiki/Instrumental_variable) and the "[Heckman correction](http://en.wikipedia.org/wiki/Heckman_correction)" (a control function approach UChicago economist James Heckman used in his Nobel-winning research on early childhood education) are good introductions.* 

*For a more technical academic reference that covers both methods, see Heckman and Navarro (2004): "[Using Matching, Instrumental Variables, and Control Functions to Estimate Economic Choice Models](http://www.mitpressjournals.org/doi/abs/10.1162/003465304323023660)".*

