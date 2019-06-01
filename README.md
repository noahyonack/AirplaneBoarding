## Simulating Times for Various Airplane Boarding Policies

#### What does this notebook do?

Given a boarding policy (that is, a rule which assigns a boarding order to passengers on a plane), this notebook simulates the amount of time it'll take to board the plane using that policy. Example policies include boarding front to back, back to front, and window-middle-aisle.

The amount of time it takes each passenger to put their luggage away and sit down is distributed ~ N(mu, sigma), where mu and sigma are defined in the code.

To create a boarding policy, subclass AbstractBoardingPolicy and fill in the abstract methods.

Then instantiate a PlaneBoardingSimulator and off you go:

```python
planeInitParams = {
    "numRows": 20, 
    "numSeatsPerRow": 6
}

policies = [
    FrontRowsFirstBoardingPolicy(), 
    BackRowsFirstBoardingPolicy(), 
    WindowMiddleAisleBoardingPolicy()
]

pbs = PlaneBoardingSimulator(planeInitParams)

# plots a histogram
pbs.plotPolicyHistogram(policies, iterationsPerPolicy=50)

or

# list of boarding times, one time per iteration
rawTimes = pbs.simulatePolicy(WindowMiddleAisleBoardingPolicy())
```