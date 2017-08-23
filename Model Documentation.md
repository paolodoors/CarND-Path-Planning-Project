# CarND Path Planning Project

## Reflection
This implementation of a path planning uses a simple approach where the car "thinks" in Frenet coordinates: it keeps track of the closest car at each side and in the current lane.

In case that the current lane is clear, the car try to accelerate to the reference speed of 49.5 mph. If the car sees another car in front, two things could happen:

1.- There's a clear path to change lanes (that is, there are no other cars at a certain distance, to avoind hit a car in front and to be hitted by a car coming from the back).

2.- There no chance to change lanes, so the car would set as a reference speed, the speed of the car in front until it could be passed.

All the math is done in Frenet coordinates and the car is shifted and rotated to start a point (x, y, theta) = (0, 0, 0) in order to make the math simpler.

The path is computed using a spline and 5 anchor points (the previous and actual position, and three forward points separated by 30 meters). Then, intermediate points are selected at a distance such it allows the car keep the reference speed.

After this computation, the points are shifted and rotated again to get then on its real (x, y, theta) values and then are sent to the simulator.
    
## Results
The car was able to drive 4.32 miles without incidents between 5 and 7 minutes, depending on the state of the traffic during each simulation. The driving is very conservative but effective. A few times, the car was hit by other cars doing unexpected lane changes or agressive accelerations, but it never hitted another car from behind.

## Future Improvements
A good improvement would be to use cost functions and finite state machines to evaluate more complex scenarios without making the code more complex.