# System-design

## Design ATM system.

## Design Uber, Ola or Lyft type of systems.
These platforms help user request rides and the driver picks them up from the location and drop them at the destination selected by the user.
### What are some of the required features?
1. Real-time service for booking rides
2. Should have the capability of assigning rides that lets the user reach the destination fast.
3. Show the ETA (Estimated Time of Arrival) of the driver after booking the ride and once the ride has been started, show the ETA of the vehicle arriving at the destination.

### What are some of the common problems encountered?
1. How to store geographical locations for drivers always on move?
2. How to assign drivers to the customers efficiently?
3. How do you calculate the ETA of the driver arrival or the destination arrival?

### Possible tips for consideration:
1. Make use of the microservices concept with fast databases for booking rides faster.
2. Evaluate Dispatch System for assigning drivers to the users.

