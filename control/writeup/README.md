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
