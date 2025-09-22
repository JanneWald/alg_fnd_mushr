# Project 2: Localization [![tests](../../../badges/submit-proj2/pipeline.svg)](../../../pipelines/submit-proj2/latest)

Replace this with your own writeup! Please place all figures in this directory.

## Question 1

The reason there more particles within a 10cm radius of the noise-free model prediction in Figure 2 than Figure 3 is because of additive noise. In our model, we only ever increase noise. For example, if you know where you are and you move, you can only ever be more uncertain where you are. (Strictly speaking with exlcusive motion model). That is why particle filtering uses the sensor readings and resampling to decrease variance of our expected position. We have to account for x, y, theta, delta, velocity all having variance.

## Question 2

Figure 1
![Initial Motion Model Setup](mm1.png)
This is the inital (POST MOVEMENT) estimation of our position. After moving up and to the left a bit. 

We can see a high degree of variance. So I changed x, y, theta, and velocity deviation from 0.05 to 0.02
![Second Motion Model Setup](mm2.png)
As seen by our distribution, our projected position is much tighter. Also observable by the visible "line like" border. 

Still a high degree of variance tho, but it is much more obvious of a widley distributed turning radius. I tested this by changing `delta_std` to 0.1

![Second Motion Model Setup](mm3.png)
Now this is very similar to the instructor result. If I wanted a tighter cone I would further reduce the standard deviation of delta.

## Question 3

The reason it is nonreallistic to claim independence is this example: If a laser hits on a wall, it is much more likely that the next closest laser will also hit a wall. This violates the typical depenence quality P(A | B) = P(A).If we treat correlated beams as independent evidence, the filter can double-count information.

The reason that our model is helps against this is with normalization and weighting. Normalizing helps by making every beam is a valid probability distribution. Furthermore, we can down tune some sensors that are "overperforming".

## Question 4

![Initial Sensor Model Setup](sm1.png)
This is our inital sensor model with default weight tuning. The obvios difference is that we seem to be overly confident where we are. The instuctor example has a decent vertical streak and a good glow around the spot. I am going to try setting `hit_std` much higher to 20.5

![Second Sensor Model Setup](sm2.png)
Obviously its much higher. Here we see that the sensor model is not super sure and shows a gaussian spread from its believed position. 

I will be changing the deviation much lower to 2

![Third MotSensorion Model Setup](sm3.png)

This version is a bit noisier and if you zoom in you can see a faint vertical streak, this is because it is unsure where is since the sensor is maxing out without a world border as it looks east.

## Question 5

![Third MotSensorion Model Setup](mazesensor.png)
