## Observations
```java
class Observations {
    //Forklift observations
	double[] forklifts_self = getObs_Forklift_selfOnly(agentId);
	double[] forklifts = getObs_Forklift(agentId);
	//Manufacturing center observations
	double[] supermarkets = getObs_supermarket();
	double[] w_inventory = getObs_workstation_inventory();
	double[] w_process = getObs_workstation_processProgress();
	
	double time = time() / getEngine().getStopTime();
	double isAgent0 = agentId == 0 ? 1 : 0;
	double isAgent1 = agentId == 1 ? 1 : 0;
	double isAgent2 = agentId == 2 ? 1 : 0;
}
```

## Metrics
```java
class Metrics {
    //collective rewards
    double totalThroughput = throughput;
    double p1 = throughput_product1;
    double p2 = throughput_product2;
    double p3 = throughput_product3;
    double imbalance_pen = imbalance_prods;
	//double fullConveyor = fullFinishConveyor;
	//individual rewards
	double essentialDelivery = forklifts.get(agentId).essentialDelivery;
	double essentialPickup = forklifts.get(agentId).essentialPickup;
	double trips = forklifts.get(agentId).trips;
	double tripDuration = time() - forklifts.get(agentId).startTrip;
	double aveTripDuration = forklifts.get(agentId).avgTripDuration(); 
	double emptyOrigins = forklifts.get(agentId).emptyOrigins;
	//double fullQueue = forklifts.get(agentId).fullQueue;
	double invalid = forklifts.get(agentId).invalidAction;
	double forkliftUtilization = forklifts.get(agentId).resourcePool.utilization();
	double timeToPickup = forklifts.get(agentId).travelToPickupTime;
    
}
```

### Collective metrics
Metric| Description
--- | --- 
totalThroughput | Sum of p1, p2 and p3 throughput
p1 | Product 1 throughput
p2 | Product 2 throughput
p3 | Product 3 throughput
imbalance_pen | Penalizes the agent by the difference between lowest and highest throughput (updateProdBalance())
***
### Individual metrics
Metric| Description
--- | --- 
essentialDelivery | sendTo_-action supplied or sent product to a WS that needed it (no priority on amount)
essentialPickup | sendTo-action picked up a product at a WS with finished product (no priority on amount)
trips | The number of trips taken by the forklift
tripDuration | The avg duration of all trips
emptyOrigins | sendTo-action attempts to pick up supply or product at empty locations (already assigned product is also considered empty)
fullQueue | sendTo-action attempts to drop off at WS with a full conveyor
invalid | sendTo-action attempts to send product to invalid WS (not following the flow pattern)
forkliftUtilization | Utilization
timeToPickup | Duration (sec) from seizing forklift to pick-up at WS or supermarket

***

## Actions

```java
class Actions {
	//4 supermarket pickup points + 7 workstations
   @Discrete(n = 11, size = 1) int origin; 
   @Discrete(n = 7, size = 1) int destination_machine;
   
   @Discrete(n = 4, size = 1) int home_location;
   
   void doIt() { doAction(origin, destination_machine, home_location, agentId);};
}
```

### *```home_location```
The ```home_location``` is one of four potential return Nodes the forklift can be assigned to when released. Our goal is to make the pickup-time and travel distance as low as possible while achieving a high throughput for all product types.