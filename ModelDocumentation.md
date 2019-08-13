# Model Documentation

This file contains the documentation for the **Udacity PID-Control Project**.

## Task Description

The goal in this project is to **revisit the lake race track from the Behavioral Cloning Project to implment a PID controller in C++ to meneuver the vehicle around the track**. The speed limit has been increased from 30 mph to 100 mph.

#### What's a PID controller

A **proportional–integral–derivative controller** (PID controller) is one of the most common control loop feedback mechanisms. A PID controller continuously calculates an **error function** (which in our case is the distance from the center of the lane) and applies a correction based on proportional (P), integral (I), and derivative (D) terms.

#### Choosing PID Parameters
The behavior of a PID controller depends on three main parameters, namely the **proportional**, **integral** and **derivative gain**. Each one of these three parameters controls the strenght of the respective controller's response. In particular:
1. **Proportional gain** regulates how large the change in the output will be for a given change in the error. If the proportional gain is too high, the system can become unstable (see *p controller* gif above).
2. **Integral gain** contributes in proportion to both the magnitude of the error and the duration of the error. In this way controller is able to eliminate the residual steady-state error that occurs with a pure proportional controller (*i.e.* a purely proportional controller operates only when error is non-zero) and is able to deal with systematic biases.
3. **Derivative gain** decides how much the error's rate of change is taken into account when computing the response. In other words, if the desired setpoint is getting closer (= error is decreasing) the response must be smoothed in order not to overshoot the target. Derivative component benefits the system's stability and settling time.

In the current project, parameters have been manually tuned by qualitatively inspecting the driving behaviour in the simulator in response to parameter's changes. Parameter's validation could also be easily performed automatically in a simulator in which headless mode was available.

## Rubric

Here's the rubric criteria along with explanation.

**Describe the effect each of the P, I, D components had in your implementation.** 

Here's are the values used for P, I, D

| Components    | Values  |
| --------------|---------|
| Kp | 0.1 |
| Ki | 0.0001 |
| Kd | 1.0 |

Proportional term Kp steers harder the further away we are from the desired trajectory. Kp alone causes oscilation which is not desirable property so the additional term is needed - Kd.

Differential term Kd is the resistance if the car is moving to quickly toward the desired trajectory line.

Ki is the integral term : adjust to the bias in the system.

**Describe how the final hyperparameters were chosen.**

Manual tuning has been used. First, tune proportional component Kp, the other terms are zeroed. After I minimized oscilation I started to tune differential term Kd. At the end, integral term Ki has been tuned.

**The vehicle must successfully drive a lap around the track.**

![PID Control Image](/screens/PIDControl.PNG) 

Please find the video here. 

[PID Control Video](/video/PIDControl.mp4) 