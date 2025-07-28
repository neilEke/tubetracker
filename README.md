# tubetracker
Have you ever wanted to know exactly where all the tube trains are at this moment, or maybe where exactly the next tube is?

My inner-nerd did, so I looked at what was available on the Internet and I found a few good examples but I was able to pick fault at them at the same time. 

LondonUnderground.live is great but it only shows a train is moving between stations, when potentially it could be 2 or more on the longer runs between stations. 

## Investigating data sources

I found that through an API that is available from TfL via their open data service you can return the approximate time to arrival of all the trains due to a particular station on a particular line, but more importantly where it was too. 

For instance, if I search for the Victoria Line at Victoria Station, I could see all the trains due into either platform (Northbound or Southbound) over the next few minutes. 

That's OK, but that's just one station on one line, I hear you say. So why don't we just get all the stations on all of the lines. 

The problem is that a particular train is due at the next station in 100seconds but it will also be due at the station after that in 220seconds and so on and so on. So we would ensure that we do not duplicate data. Additionally, we need to ensure we catch every train but not to many to reduce the number of duplicates. 

The London Underground at peak times has nearly 600 trains each of them potentially sending in data about it's track position every 6 or 7 seconds (rough observation). 

So my first step is going to be to create a tube logger, that can log the position/location of the train and the time it sent it to gather a picture of the actual track layout. 


## Data Logging

I need to build a data logger that can capture details for each train, the block it is in, the time it started in that block. When the train passes into the next block, the finish time can be subtracted from the start time of that block and a 'time in block' value is obtained. By logging the order of blocks I can then calculate the location of each block on the network.

### Data Anomalies - to be dealt with
Most lines on the map by cartometro have track-points at termini, offering multiple platforms that trains could arrive on/depart from.
Trains can enter/leave the 'passenger network' into depots, normally only at the start and end of its duties via points.
Trains can terminate early and use turning track-points to swap ends and return.


