# Beam-Timely-Stateful-Processing

## Problem Statement :

Consider customer is doing some shoping and you have 2 unbounded events say X, Y getting generated. For any customer , X will generate only once but Y will generate more than once (offcourse the data varies with each Y type of events). These events are connected/related to each other with some unique identifier say u-id. And Y's will be generate only when X is generated and that too with 30mins of duration. Assume both the events are coming on separate pubsub topic. 
Make sure no dataloss should be happen.
Points to be consider data ingestion would be in huge number and need to handle out-of-order events.

## Solution : 

Apache beam provides Timely-Stateful processing
Refer : 
- https://beam.apache.org/blog/stateful-processing/
- https://beam.apache.org/blog/timely-processing/

When first events come, put it into state and register session timeout timer( here it is 300mins). And first event can be anything either X or Y.
And process the events as they come and keep on updating the state. Once timer gets expired, compute the result in the session and delete the state.
And we will create the value state for each of the events.


## Various other Use cases :
- Mobile Gaming
- Mobile Banking
- Ecommerce Shopping Experience
- Time Series Data




