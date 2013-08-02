---
layout: post
title: "Why Bus Crowding Happens, and How Data Can Help"
author: Juan-Pablo Velez
pic: "cta-header.jpg"
pic-credit: [Ben Husmann via flickr](http://www.flickr.com/photos/benhusmann/4728778887/)
---

We've all been there, in big cities far and wide: standing at an intersection, waiting for the bus to come. Passengers keep arriving at the stop, and you start to realize you could have a crowded ride ahead.   When the bus finally arrives, it's packed.   Should you wait for the next bus?  Or will it be just as crowded --- or possibly more so? You squeeze on anyway and ritualistically curse the transit gods.

<a href="http://www.transitchicago.com/"><img src="/img/partners/cta.jpg"></a>	

The Chicago Transit Authority (CTA) is acutely aware of this crowding problem and the frustration it causes to riders. In fact, the transit agency has been trying to tackle the problem of how best to allocate its bus and rail services for years - and was one of the first to use big data to inform these decisions. Last year, the CTA launched a [crowding reduction initiative](http://www.transitchicago.com/news_initiatives/projects/decrowding.aspx) to address the problem by re-allocating bus service where it’s needed most. 

Data is at the heart of understanding the crowding problem: from an operations standpoint, you have to know where the buses are to know whether gaps in service are causing crowding at stops and on buses.  From a scheduling perspective, you need to know how many people want to ride a route in order to know how many buses to run.

So why does crowded transit persist? Because it's a really hard problem to solve. Luckily, there are vast quantities of data that can be harnessed in many ways.  

That's where we come in - we're developing new simulation tools that will help the CTA predict the impact of changes in service (whether changes in the schedule itself or changes to reliability) on the crowding of a route.  

#### Why Crowding Happens
First, we need to understand why buses can get crowded in the first place:

<img src="/img/posts/crowded-bus.png">
pic-credit: [Dane Brian via flicker](http://www.flickr.com/photos/12955651@N07/7298151730/)

- ** Transit service capacity**: The buses scheduled to run a route at a given time have a certain total combined capacity. As the number of people seeking to ride approaches this capacity, buses will predictably get more and more crowded unless additional bus trips are added to the schedule.  If the ridership demand exceeds capacity, riders can get left behind at bus stops.

- **Service gaps/bus bunching**: Even if there are enough buses scheduled to accommodate passenger demand, a large gap in service can also cause riders on the route to experience crowding.  If buses aren’t spaced evenly along the route, then particular buses will carry a disproportionate share of the total riders, meaning certain buses will be crowded, while others will be underutilized. 

Here's how it often happens:  when a bus falls behind its schedule -- say, due to a combination of road traffic, hitting every red light, and a few stops with more riders than usual  -- the stops ahead along the route accumulate more waiting riders than they usually would between buses.  When these additional passengers board the late bus, it becomes more crowded than if it had stayed on schedule, as some of its on-board passengers would have caught the following bus.  

Furthermore, the likelihood that at least one passenger is waiting at each and every bus stop increases as the gap between buses widens; normally, a bus can expect to skip some number of lower-ridership stops where no one is waiting to board.  Likewise, more riders on board increases the likelihood of someone wanting to get out at each stop. You get a negative feedback loop: additional passengers accumulate, the bus gets more crowded, it stops more often, and falls even further behind. Eventually, an on-time bus following behind it is likely to catch up, creating a bunch. 

#### Fighting over-crowding with data
Depending on the root causes, transit agencies can generally take one or more of the following  actions to reduce crowding:

- They can run more buses on a route, by re-allocating them from another route. 

- They can adjust the schedules of individual bus trips if there are predictable and consistent patterns of a particular bus getting crowded or falling behind schedule.

- They can take operational steps to reduce deviations from the schedule. This may involve field supervisors making on-the-fly changes once buses are in service: for example, ensuring drivers start their scheduled service on time and don't drive too quickly or slowly, deploying buses to fill gaps that emerge on the route, and more.

In order to inform these decisions, the CTA has spent over a decade installing sensors - vehicle location systems (e.g. GPS) and passenger counters - on its bus fleet.  In addition to feeding real-time location data to support its [CTA Bus Tracker API](http://www.transitchicago.com/developers/bustracker.aspx), this generates a massive volume of historical data that can be analyzed to detect patterns.  

#### Counting people
The CTA has long counted how many passengers get on and off Chicago's buses. From the old days of tokens to the present day of magnetic stripe and smart cards, the fare collection process has provided CTA data on how many riders in total get on a given route.  While those total ridership figures are critical, they don’t directly convey information about route crowding, i.e. how many riders are on each bus at a given point on the route. 

<img src="/img/posts/paper_data.jpg">

That data used to be collected by hand. This is a sample of analogue passenger count data from the fall of 1975. The agency deployed workers to locations along every route who tallied the riders passing by during the morning and evening rush periods.

These days, the [buses themselves](http://www.wbez.org/series/curious-city/question-answered-what-factors-lead-cta-bus-routes-being-added-or-removed-102076) do the counting. Using a pair of infrared beams positioned at both the front and rear doors, they silently record an "on" when you board the bus and an "off" when you alight. These data are recorded in conjunction with vehicle location history data, so recorded “ons” and “offs” are tied to each stop along the route. The data are then saved to a hard drive on the bus, and uploaded to a central server each night when the bus is back at the garage.

By keeping track of how many passengers are getting on and off, we can estimate the number of people *in* the vehicle when it leaves every stop. Here's an example of what that looks like for one trip from the South Side to the Loop on the #6 Jackson Park Express bus on a Sunday morning in early 2013:

<img src="/img/posts/load-plot.png">

Eleven riders board the bus as it starts the route in the Woodlawn neighborhood. More people leave than board between 66th and 65th streets, perhaps due to a nearby Metra commuter train station. The bus gains passengers again as it passes by the University of Chicago in Hyde Park. It absorbs passengers as it winds its way through the neighborhood, until it gets on Lake Shore Drive and drives express to downtown. Once in the Loop, the bus sheds riders as they head off to their jobs or transfer to ‘L’ trains.

The number of passengers inside a bus - or *bus load*, in CTA parlance - is a great way to measure bus crowding, and it's the metric that the agency's crowding reduction efforts seek to minimize.

To determine the right number of buses needed to keep bus loads below a certain threshold, we need to measure how many people are riding the route as a whole at that time of the day. And bus load alone would be an incomplete way to measure passenger demand, because the number of people in the bus is affected by how often buses run.

To understand why, imagine a route with only two stops.  A total of 50 people arrive randomly at the first stop during each half hour. If the bus comes just once per half hour, its load will be 50 when it leaves the stop. If a bus comes every 15 minutes, however, the departing bus load would be 25. Each bus will be half as crowded, even though the same number of people rode the route during that half hour.

### How CTA tackles crowding
To measure passenger demand independent of bus frequency, the CTA instead examines the *flow* of a route - the total number of people riding by a stop in a particular time period. The passenger flow for every stop along the route is calculated by adding up the people inside every bus that passed by a particular stop during that time period.

<img src="/img/posts/flow-plot-1day.png">

Here's the flow for the #6 bus route between 8-8:30 am on that same Sunday morning in early 2013. During those thirty minutes, two more buses traveled the route after the one we followed above. The green line represents the combined total number of riders that passed by each stop on those buses.

Next, the CTA identifies the busiest stop in the route - the area of "peak flow". This is the stop through which the most bodies are being moved at that time of the day - the Balbo & Columbus stop, in our example.

The passenger flow at this “maximum load point” is the main determinant of how many buses are needed to achieve a certain target crowding level, or bus load. Once you locate it, it's easy to figure out how many buses need to serve that location during that time window: take the total number of people passing by that stop, divide them by the maximum number of people you'd like to have on each bus, and you'll get the minimum number of buses needed to “decrowd.”

There's  a significant challenge here, however.   In practice, the number of people riding the route fluctuates every day, affected by all kinds of external forces - the day of the week, the time of year, the weather, school and office schedules, nearby sporting events, and more. It will vary day by day, week by week, and it will also change over time as neighborhoods and people’s commuting habits change.  There's no single, constant peak flow - rather, there are many:

<img src="/img/posts/flow-plot-jan.jpg">

Every point on this chart represents the daily flow at a stop at the same time of day over an entire month. We've simply taken the flow chart from above for each day, and piled them all on top of each other. [day from first chart was low flow -- a Sunday]  A clear trend emerges - the flow dips after Woodlawn, picks up through Hyde Park and Kenwood, and falls in the Loop.   

CTA has different service schedules for each day of the week, which can generally be grouped into three overall service patterns: Weekdays, Saturdays, and Sundays/Holidays.  There is usually at least *some* consistency as to the flow on these particular “day types” but even so, there can be significant variability.

If the flow changes day by day, how do we decide how many buses to schedule?

- We could play it safe and run enough buses to serve the highest peak flow of the month. But this would be inefficient:  the vast majority of days are less busy, and there are only so many buses and drivers available to deploy.  

- We could target service levels based on the average flow at each stop (the orange line in the chart below), but then buses will likely be overcrowded around half of the time.

There's a trade-off between reducing crowding and spending more money, so we need a practical way to balance these extremes. CTA also applies [Service Standards](http://www.transitchicago.com/assets/1/miscellaneous_documents/servicestandards129737.pdf) [pdf], which set overall policy objectives for its bus service, including minimum service levels and spans of service (first bus/last bus times) to ensure access to the system, minimum cost effectiveness ratios (fare revenue over operating costs), and so on.

In practice, the CTA uses the 75th percentile passenger flow as a balance to ensure that buses are usually neither overcrowded nor underutilized, with some slack for service variability:
 
<img src="/img/posts/flow-plot-percentile.png">

But there may be a better solution. The vast quantities of vehicle location and passenger count data --- and simulation based upon them --- offer the potential to predict crowding along a route before it develops.  In particular, a simulation calibrated with historical variability in ridership and service would enable predictions of how changes to a route’s reliability and/or schedule affect its crowding levels. Such a model could help CTA make proactive and flexible service decisions that anticipate changes in ridership and reduce crowding before it starts.

That's the model that the fellows on the CTA team are working on this summer, which we will cover in detail in our next post. 

 
 
 

