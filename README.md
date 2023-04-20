# Edge Status Aggregator 
Edge Status Aggregator watches and processes the NFDeployment custom resources. It runs on Nephio's management cluster.

## Description
Edge Status Aggregator(ESA) watches and processes Nephio's NFDeployment custom resources. The primary goal of ESA is to track and aggregate statuses of different NF instance's deployment.
EdgeStatusAggregator takes the topology information from NFDeployment CR, and builds a relationship graph to track each individual NF specific status. 
The changes in any individual status is reflected on NFDeployment's CR status.
