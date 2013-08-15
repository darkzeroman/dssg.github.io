---
layout: post
title: "Divvy: Helping Chicago's New Bike Share Find Its Balance"
author: Jette Henderson with Adam Fishman
pic: "divvy-header.jpg"
"pic-credit": juggernautco
published: true
---

“Wow! What is that? Where’d you get it?,” the beach-going twentysomething asked me. I looked up from the map on my phone and steadied the powder-blue bike under me to answer his question. It was, of course, a Divvy bike - part of Chicago’s hot new bike share system. 

As a car-less visitor in Chicago, I spent the first month of the fellowship relying on my feet  and the public transit feature of Google Maps to get around the city. After Divvy launched in early July, the city felt much smaller. 

That day, I had picked up a bike on Ohio St. just west of Lake Shore Drive. After riding for two minutes to get to the beach, I was trying to figure out how to spend the twenty-eight minutes remaining on my pass before returning my bike at a Divvy station somewhere else in the city. We chatted a bit more about bike share, and he wandered off to play beach frisbee while I hit the Lake Shore Trail to spend my remaining twenty-four minutes. 

The beachgoer was not the first stranger to ogle my Divvy bike that day. I rode away satisfied that I was able to evangelize for the Divvy program while taking the afternoon off from the Data Science for Social Good project -- with Breanna Miller, Hunter Owens, Juan-Pablo Velez, Walter Dempsey, Adam Fishman, and Vidhur Vohra -- to help Divvy run more smoothly. 

<a href="http://http://divvybikes.com//"><img src="/img/partners/divvy.jpg"></a>	

#### The Rise of Bikeshare
Bikeshare allows people to hop on one of 4,000 bikes at one of 400 stations, take a short trip, and drop the bikes off at another station. In doing so, the system expands the options of commuters. Given the radial layout of the El, as you move farther away from downtown, the more likely is is that you have a long walk to a stop. Divvy is perfect for those short one-way trips and has the potential to make commutes or travel at any time of the day much simpler. It’s also great for quick hops around the neighborhood.

In addition to making it easier to get around cities - what transportation researchers call mobility - bikeshare is good for road congestion, the environment and people’s health. Because it makes trains and buses easier to reach, it can induce people to switch their commute from driving to transit, leading to less traffic and fewer greenhouse gases. And biking burns more calories than the sedentary exercise of sitting in a car. 

Chicago’s bike share is new, but programs like it have been popping up all over the world since 2007. Velib’, the bike share program in Paris, has over 24,000 bikes in its system. New York City’s Citi Bike program, which barely edged out Divvy with its launch this past May, is the largest in the US. Oliver O’Brien, a research associate at the University College of London, created the map below to show the location and size of bike share programs around the world. 

<a href="http://bikes.oobrien.com/global.php"><img src="/img/posts/global-bike-map.png"></a>	

As these bikeshare programs grow in popularity, they converge upon a common problem. The flow of commuting residents often means that more people bike in one direction than in the other at different times of the day. In Chicago, the majority of commuters travel from outlying neighborhoods into downtown Chicago in the morning, and then back to those neighborhoods in the evening.

Commuters might face a problem in the morning when they try to dock their bikes only to find the station is full. In the afternoon, they might leave work and find no bikes to ride at the corner station. Bike share companies call this mismatch between the expectations of the rider and the reality of the station a “balancing” problem. 

We can see this trend in the following graph that shows the average number of bikes at two [Capital Bikeshare](http://www.capitalbikeshare.com/) stations in Washington D.C. over the course of a day. The averages were taken for every Monday over a year-long period. 

<img src="/img/posts/divvy-graph.jpg">

In the mornings, commuters check out bikes from the residential station (the green line) and ride them to the train station or downtown, which corresponds to the steep decline starting around 7 am. As bikes leave the residential station, they start piling up at the downtown station between 7 and 9 am. In the afternoon, we see the reverse trend as the number of bikes plummets at the downtown station (the purple line) and commuters ride back home. On this day, the number of bikes at the residential station in the evening does not return all the way back to morning levels, suggesting commuters might not be as likely to ride home from work as they are to ride to work.

For most of the day, people using the bikeshare system will probably be able to find an available bike at any station, and find an open slot to dock the bike at the end of their ride. But in the middle of the day, the residential station may be empty of bikes, and even if the rider finds one, the downtown station may be full when they get there.

Divvy and other bikeshare companies solve the balancing problem by driving trucks around the city, picking up bikes from full stations, and redistributing them to less crowded locations.

<img src="/img/posts/divvy-truck.jpg">
Photo by [Daniel X. O'Neil](http://www.flickr.com/photos/juggernautco)

The trouble with the this solution is that there is no great way to plan routes for the trucks. Right now, Divvy and other bike share dispatchers use real-time information about the number of bikes at each station to figure out where to redistribute bikes. Here's what they see in DC's Capital Bikeshare system:

<img src="/img/posts/dc-bike-dashboard.png">

They simply look at which stations are currently full or empty, and how long they’ve been that way. Then they move bikes into or out of these stations first.

In other words, they work by reacting to the current state of the system rather than predicting where to go in the future.

#### Proactive Re-balancing
Our goal is to help bike share companies anticipate where full and empty stations will be one hour ahead of time. To this end, we are [building predictive models](www.github.com/dssg/bikeshare) that use current information - such as the number of bikes currently at a station, time of day, day of the week, and weather - as well as historical data to produce a prediction of how many bikes will be at each station in sixty minutes. 

We will package this prediction model in an easy-to-use map interface for Divvy, which will display the stations on a map and color code them based on how empty or full the model predicts them to be. A dispatcher can look at this presentation and quickly assess and direct the system’s rebalancing needs.

This tool will help Divvy anticipate rebalancing issues before they arise. Divvy has already expanded the transportation options for people in Chicago, and we want to keep this service running smoothly as it spreads across the city. Hopefully, when seeing a Divvy bike is no longer be a novelty to Chicagoans, finding one won’t be either.

<img src="/img/posts/divvy-dock.jpg">
Photo by [Daniel X. O'Neil](http://www.flickr.com/photos/juggernautco)