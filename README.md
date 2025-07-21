# tubetracker
Every wanted to know exactly where your next tube is and how long your going to have wait for it to arrive. My inner-nerd did, so I looked through all the APIs available from TfL and found that one returns it's exact signalling block. 

Whilst this information in its raw form doesn't mean a lot, I thought if I set up a data logger, I could calculate how many blocks the train is away, the length of time the train is in each of them blocks and ultimately how long before the doors should be opening. 

## Phase One: Data Logging

I need to build a data logger that can capture details for each train, the block it is in, the time it started in that block. When the train passes into the next block, the finish time can be subtracted from the start time of that block and a 'time in block' value is obtained. 

By logging the order of blocks I can then calculate what block is where on the network. There may be some data anomalies which would need ironing out as they happen. In addition, trains arriving at terminus or multi-platform/destinations pass over points, which would need to be taken into account. 

