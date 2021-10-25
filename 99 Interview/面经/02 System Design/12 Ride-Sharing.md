# Reference
[# Designing Uber backend - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/YQVkjp548NM)


# Introduction
Applications: Uber, Lyft, Didi, Via, Sidecar, etc.

## Key Words
Write Heavy


# Requirements
## **Functional**
- Drivers regularly notify the server to update their current location and availability to pick passangers
- Passengers can see all nearyby available drivers
- Passengers can request a ride, and nearby drivers are dispatched.
- Once the offer is accepted or assigned, drivers and passengers can share their current location with each other

## **Non-Functional**
Highly available
Low latency

# Estimation
## **Traffic**
## **Storage**
---
# High Level Design



# Follow-up
How should we rank the nearby drivers and dispatch a driver to the passenger?
- Ranking based on ETA. The drivers will be pushed into a service to calculate the ETA to the passenger, and the shortest ETA  driver is dispatched to the passgener.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMzgyMjQ2NjRdfQ==
-->