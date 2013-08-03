---
layout: post
title: "Why Bus Crowding Happens and How Data Can Help"
author: Juan-Pablo Velez and Andres Akle Caranaza
pic: "cta-header.jpg"
pic-caption: "A CTA bus arrives at the Oak Park Blue Line station."
pic-credit: benhusmann
---

We've all been there: standing at an intersection, waiting for the bus to come. Passengers keep arriving at the stop, and you start to realize you could have a crowded ride ahead. When the bus finally arrives, it's packed. Should you wait for the next bus? Or will it be just as crowded - or possibly more so? 

<a href="http://www.transitchicago.com/"><img src="/img/partners/cta.png"></a>	

The Chicago Transit Authority (CTA) is acutely aware of this crowding problem and the frustration it causes to riders. In fact, the transit agency has been trying to tackle the problem of how best to allocate its bus and rail services for years - and was one of the first to use big data to inform these decisions. Last year, the CTA launched a [crowding reduction initiative] (http://www.transitchicago.com/news_initiatives/projects/decrowding.aspx) to address the problem by re-allocating bus service where it’s needed most. 

Data is at the heart of understanding the crowding problem: from a scheduling perspective, you need to know how many people want to ride a route in order to know how many buses to run. Once the buses are on the road, you have to know where the vehicles are to see whether they’re bunching and causing crowding at stops and on buses. 

That's where the Data Science for Social Good fellowship comes in. Fellows Walter Dempsey, Andres Akle Caranza and Jordan Bates and mentor Brandon Willard are developing new modeling and simulation tools that will help the CTA predict the impact of running more or less buses on the crowding of a route.  

#### Why Crowding Happens
First, we need to understand why buses can get crowded in the first place:

<img src="/img/posts/crowded-bus.jpg">
*[Dane Brian via flicker](http://www.flickr.com/photos/12955651@N07/7298151730/)*

- **Number of buses on a route**: The buses running a route at a given time have a certain total combined capacity. As the number of riders approaches this capacity, the buses will get more and more crowded unless additional bus trips are added during that timeframe. If riders *exceed* this capacity, they can get left behind at bus stops.

- **Gaps between buses**: Even if enough buses are running to accommodate passenger demand, a large gap between vehicles can also cause riders on the route to experience crowding. If buses aren’t spaced evenly along the route, then particular buses will carry a disproportionate share of the total riders, meaning certain buses will be crowded while others will be underutilized. 

Here's how it often happens: when a bus falls behind its schedule - due to a combination of road traffic, hitting every red light, or a few stops with more riders than usual - the stops ahead along the route accumulate more riders than they usually would between buses. When these additional passengers board the late bus, it becomes more crowded than if it had stayed on schedule, as some of these passengers would have caught the following bus. 

As the gap between buses widens, the likelihood that at least one passenger is waiting at each and every bus stop increases; normally, a bus can expect to skip some number of lower-ridership stops where no one is waiting to board. Likewise, more riders on board increases the likelihood of someone wanting to get out at each stop. 

The bus stops more frequently, and falls further behind, creating a negative feedback loop: additional passengers accumulate, the bus gets more crowded, it stops more often, and falls even further behind. Eventually, an on-time bus following behind it is catches up, creating a bunch.

#### Fighting over-crowding with data
Depending on the root causes, transit agencies can reduce crowding by taking one or more of the following actions:

- They can run more buses on a route by re-allocating them from another route. At CTA, this is done by planning department, and it’s the piece the fellows are focusing on.

- They can reduce gaps between buses. This may involve field supervisors making on-the-fly changes once buses are on the road: for example, ensuring drivers start their scheduled service on time and don't drive too quickly or slowly, deploying buses to fill gaps that emerge on the route, and more.

In order to inform these decisions, the CTA has spent over a decade installing sensors - GPS and passenger counters - on its bus fleet.  In addition to feeding real-time location data to support its [CTA Bus Tracker API](http://www.transitchicago.com/developers/bustracker.aspx), this generates a massive volume of historical data that can be analyzed to detect patterns. 

#### Counting people
The CTA has long counted how many passengers get on and off Chicago's buses. From the old days of tokens to the present day of magnetic stripe and smart cards, the CTA has collected data on how many people are riding a given route through the fare collection process. While those total ridership numbers are critical for planning bus service, they don’t tell you anything about route crowding, i.e. how many riders are *on* each bus at a given point on the route. 

<img src="/img/posts/paper_data.jpg">

That data used to be collected by hand. This is a sample of analogue passenger count data from the fall of 1975. The agency deployed workers to bus stops along every route, who then tallied the riders passing by during the morning and evening rush hours.

These days, the [buses themselves](http://www.wbez.org/series/curious-city/question-answered-what-factors-lead-cta-bus-routes-being-added-or-removed-102076) do the counting. Using a pair of infrared beams positioned at both the front and rear doors, they silently record an "on" when you board the bus and an "off" when you alight. Using GPS, these “ons” and “offs” are tied to each stop along the route. The data are then saved to a hard drive on the bus and uploaded to a central server each night once the bus returns to the garage.

By keeping track of how many passengers are getting on and off, we can estimate the number of people *in* the vehicle as it leaves every stop. Here's an example of what that looks like for one trip from the South Side to the Loop on the #6 Jackson Park Express bus on a Sunday morning in early 2013:

<img src="/img/posts/load-plot.png">

Eleven riders board the bus as it starts the route in the Woodlawn neighborhood. The bus gains passengers as it passes by the University of Chicago in Hyde Park. It absorbs passengers as it winds its way through the neighborhood, until it gets on Lake Shore Drive and drives express to downtown. Once in the Loop, the bus sheds riders as they head off to their jobs or transfer to ‘L’ trains.

The number of passengers inside a bus - or *bus load*, in CTA parlance - is a great way to measure bus crowding, and it's the metric that the agency's crowding reduction efforts seek to minimize.

To determine the right number of buses to run to reduce crowding, we need to measure how many people are riding the route *as a whole* at that time of the day. And bus load is a bad way to measure overall passenger demand, because the number of people in the bus is affected by how often buses run.

To understand why, imagine a route with only two stops. A total of 50 people arrive randomly at the first stop during each half hour. If the bus comes just once per half hour, its load will be 50 when it leaves the stop. If a bus comes every 15 minutes, however, the departing bus load would be 25. Each bus will be half as crowded, even though the same number of people rode the route during that half hour.

#### How CTA tackles crowding
To measure passenger demand independent of bus frequency, the CTA instead examines the *flow* of a route - the total number of people riding by a stop during a particular time period. 

A bus stop’s passenger flow is calculated by adding up the people inside every bus that passed by that stop during the time period. The CTA does this for every stop on every route in the system.

<img src="/img/posts/flow-plot-1day.png">

Here's the flow for the #6 bus route between 8:00 and 8:30 a.m. on that same Sunday morning in early 2013. During those thirty minutes, two more buses traveled the route after the one we followed above. The green line represents the combined total number of riders that passed by each stop on those three buses.

Next, the CTA identifies the busiest stop in the route - the area of "peak flow". This is the stop through which the most bodies are being moved at that time of the day - the Balbo & Columbus stop, in our example.

The passenger flow at this “maximum load point” is the main determinant of how many buses must be run to achieve a certain crowding level, or bus load. Once you locate it, it's easy to figure out how many buses need to serve that location during the time window: take the total number of people passing by that stop, divide them by the maximum number of people you'd like to have on each bus, and you'll get the minimum number of buses needed to “decrowd.”

There's a significant challenge here, however. In practice, the number of people riding the route fluctuates every day, affected by all kinds of external forces - the day of the week, the time of year, the weather, school and office schedules, nearby sporting events, and more. Ridership will vary day by day, week by week, and it will also change over time as neighborhoods and people’s commuting habits change. There's no single, constant peak flow - rather, there are many:

<img src="/img/posts/flow-plot-jan.png">

Every point on this chart represents the daily flow at a stop between 8:00 and 8:30 a.m. over an entire month. We've simply taken the flow chart from above for each day, and piled them all on top of each other. A clear trend emerges - the flow dips after Woodlawn, picks up through Hyde Park and Kenwood, and falls in the Loop.   

CTA has different bus schedules weekdays, Saturdays, and Sundays/holidays.  There is usually *some* consistency in the flow patterns of these “day types,” but there can be still be significant variability.

And that’s the problem: if the flow changes day by day, how does CTA decide how many buses to schedule?

- We could play it safe and run enough buses throughout the month to serve the day with the highest peak flow. But this would be inefficient: the vast majority of days are less busy, and there are only so many buses and drivers available to deploy.  

- We could schedule buses based on the average flow at each stop (the orange line in the chart below), but then vehicles will likely be overcrowded around half of the time.

There's a trade-off between reducing crowding and spending more money, so we need a practical way to balance these extremes. 

In practice, the CTA uses the 75th percentile passenger flow<sup>1</sup> as a balance to ensure that buses are usually neither overcrowded nor underutilized, with some slack for service variability. The 75th percentile line for weekday traffic during January 2013 is shown in green below:
 
<img src="/img/posts/flow-plot-percentile.png">

But there likely is a better solution. The vast quantities of vehicle location and passenger count data can probably allow us to predict crowding along a route before it develops.  

Bus service simulations - reflecting the natural variability in ridership and service - would allow the agency to forecast how adding or removing service on a route might affect its crowding levels. These statistical models could help CTA make proactive service decisions that anticipate changes in ridership and reduce crowding before it starts. 

That's the model that the fellows on the CTA team are working on this summer, which we will cover in detail in our next post. 

 1. The CTA also applies [Service Standards](http://www.transitchicago.com/assets/1/miscellaneous_documents/servicestandards129737.pdf) (pdf), system-wide policy objectives for its bus service that govern minimum service levels, hours of operation, and more. These objectives exist to ensure that the agency can provide widespread access to buses while maintaining a cost-effective service.


 

