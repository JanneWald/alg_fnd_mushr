# Project 3: Control [![tests](../../../badges/submit-proj3/pipeline.svg)](../../../pipelines/submit-proj3/latest)

by Janne Wald
CS4963

## Question 1

First I had to get a baseline of algorithm with $K_p = K_d = 0.5$
![New Map](pid_base.png)
Doubling $K_p$ I got this:
![New Map](pid_double_kp.png)
Shrinking $K_p$ to `.1` I got this:
![New Map](pid_min_kp.png)
Manipulating $K_p$ clearly made the algorithm more responsive to the actual derivative of speed. With incredibly low $K_p$ it looked like it was lagging behind the plan because it wouldnt add enough speed. Thats also why it is important not to become too overzealous with a higher $K_p$ over $K_d$, because it will cause the path to overeact and oscillate over the path.

## Question 2

I underwent a manual tuning process, as seen in Question 1. I landed on $K_p = 1$ and $K_d = 0.5$. Landing a $\frac 2 3$ ratio. Making the correction matter a good chunk more. I could have tested more but I was pretty happy with the accurracy evident in these tests:

### PID Circle

![pid circle path](pid_circle.png)

### PID Left

![pid left turn path](pid_left_turn.png)

### PID Wave

![New Map](pid_double_kp.png)

## Question 3

I did another manual tuning process. I started with the base settings of `lookahead = 0.1` and was shocked.
![Base lookahead](pp_base_look.png)
We can clearly see the pitfall of a short lookahead distance. It is massively overcorrecting and is spiraling because of how incorrect the pose is at every spot(esp. since the begining pose of the car is not alligned with the desired path). I would continually, but safely, increase the lookahead value.

I increased it up to 1, where I was noticing some slight drift towards the middle. So I settled at `distance_lookahead: .75`

Even with correcting the bad starting pose it follows the wave well:
![pp wave](pp_wave.png)

## Question 4

### PP Large

In this scenario I set `distance_lookahead: 2`. This is much to large as is evident in the plot:
![pp large](pp_large.png)
Inuitvely, it makes sense that as we increase the lookahead distance, we approach the trivial solution of driving straight from point a to point b. We can see this flattening infront of us. The target point is often overshooting the apex curvature.

### PP Small

Given the default value is too small I figured it would be funny to overexagerate a small lookahead even more. `distance_lookahead: .08`:
![pp really small](pp_small.png)
Here we can see the real pitfall of a small lookahead distance. Oftentimes, it would even use a distance that is regresses on the x axis, because it was technically closer. It would take every turn at the maximum turn and it even left the final car in a pose that was impossible for it to reach the end.

## Question 5

By the nature of Pure Pursuit, it has really strong cabalities following curvatures. The radius of a circle did not change much in the performance of PP.

### Small Circle (r = 1)

![small circle](circle_small.png)
Here we can see the limits of what we would expect, any lower and we exceed the steering capabilites of the robot. Only small thing of note is the slight error we get from turning at max speed at the top of the circle. This error gets minimized again near the bottom.

### Large Circle (r = 20)

![large circle](circle_large.png)
The pixel size doesn't show the path taken but it does match it perfectly. And at large radii it can be percieved as going straight.

