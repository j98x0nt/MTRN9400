java c
MTRN9400 Control of Robotic Systems
ASSIGNMENT 1 - T3 2024
1    Overview of the Assignment
This assignment is on the control of robot manipulators and contributes  25% to your overall course grade. The submission deadline is 5:00pm on Friday, 25th October.
Assignment results will be returned within 2 weeks following the submission deadline. You are required to complete this assignment individually and submit your report to Moodle.
1.1    Learning Outcomes
This assignment specifically targets the following learning outcomes:
•  LO1: Learn robot’s kinematic and dynamical model.
•  LO2: Stability analysis and control of nonlinear systems.
•  LO3: Understand different classes of controllers and apply them to robotic systems.
2    Assignment SpecificationThe assignment is divided into three parts.  This document will explain what is required for each part and how each part contributes to your overall assignment grade.  Please use the provided MATLAB files for the simulation components of the assignment.  Please also watch the YouTube video that explains how to use these MATLAB files. A link to this video is provided in the FAQ: Assignment 1 Page on Teams.
In this assignment, you will design/analyse two different controllers for the regulation problem of a 2-DOF robot manipulator. The marks allocated to each part of the assignment are as follows:
•  Part 1 (6 marks): PD controller
•  Part 2 (7 marks): Properties of robot manipulators
•  Part 3 (10 marks): PD control with gravity compensation
•  Report presentation (2 marks): The criteria include good spelling and grammar, appropriate tech- nical language, logical structure including using headings and other conventions, appropriate graph- ical and tabular presentation, caption for graphics and tables, and appropriate spacing that aids readability.


2.1    Part 1 (6 marks)
In this part, you will control a 2-DOF robot using a PD controller:
τ = -Kp (q(t) - qd ) - Kd  ˙(q)(t).                                                      (1)
This controller is explained in Week 5 lecture and also in Chapter 6 of the Kelly’s textbook.We aim to design the PD control gains so that the controller is locally implementable, where the torque or force computed by the controller and applied to a specific joint depends only on the position and velocity of that individual joint, without being influenced by the positions or velocities of other joints. Mathematically, this is achieved by the choice of diagonal matrices Kp  ∈ R2  and Kd  ∈ R2 .To simply the gain tuning process, we further assume that all diagonal entries of each of these matrices are the same.  In other words, we assume the matrices Kp  and Kd   are in the form. of Kp  = kpI2   and Kd  = kdI2  where kp  and kd  are constant scalars to be designed and I2  ∈ R2×2  is the identity matrix.
You can simulate the PD controller in (1) on a 2-DOF robot manipulator using the provided MATLAB files.
(a)  Explain how kp  and kd  can be tuned so that
•  The joint angular position errors are small;
•  The joint angular velocity errors are zero;
•  The transient response is good (i.e., the rise time is small and there is noor little oscillations in the position and velocity errors).Add a figure similar to Figure 1 that clearly shows the transient response of the position errors and the steady-state values for the gains you chose in this part.   You may add Data Tips that show the values of the position errors.  Write the matrices Kp  and Kd  you used in your simulation.   (3 marks).

Figure 1: Settling time of PD Control with gravity compensation


(b)  Suppose we want to apply the PD controller  (1) with the gains obtained  in Part  1(a) to a real robot.  Note that in real-world experiments, the model of a robot may not be exactly the same as
M(q)¨(q) + C(q, ˙(q))˙(q) + g(q) = τ, due to, for example, measurement noises, elasticity of joints and
links, and actuator saturation.Explain what factors should be considered in the design of the gains kp  and kd  fo代 写MTRN9400 Control of Robotic Systems ASSIGNMENT 1 - T3 2024Matlab
代做程序编程语言r real-world exper- iments.  Can we use the same values/range of values we obtained in Part  1(a)?  To get a full mark for this part, you should explain at least 4 key points that should be taken into consideration.  (3 marks)
2.2    Part 2.  (7 marks)
Use the 2-DOF model given in Section 4, and
(a)  Find λm  and λM  for the inertia matrix M(q) of the 2-DOF robot example such that
0 < λmI2  ≤ M(q) ≤ λMI2 ,                                                      (2)where λm  and λM   are respectively the strictly minimum and maximum eigenvalues of M(q) which are independent of q.   You  may  either solve this part numerically or  analytically.   If you  use  a numerical method, you should include the MATLAB code you used for this part in your report with sufficient comments explaining your code.  If you use an analytic method, you need to provide a detailed explanation of your analytical solution in the report.  You only need to provide either a numerical or an analytical method for calculating the values of λm  and λM , not both.The values you estimate or calculate for λm  and λM  should be close to the real bounds. Obviously, one can find conservative values for λm  and λM  that are not really useful (say, for example, λm  = 1e−100 and λM  = 1e100). This is not acceptable.  (2 marks)
(b)  Find a constant kc  > 0 such that
ⅡC(q, ˙(q))˙(q)Ⅱ ≤ kc Ⅱ˙(q)Ⅱ2 .                                                            (3)Similarly to Part 2(a), you can use either a numerical or an analytical method to find kc. It is essential to provide a clear and detailed explanation on how you obtained your estimate of the smallest value for kc , and if you have used MATLAB for this part, include your MATLAB code in your report. Note that Equation (3) holds for all vector norms, such a 1-norm, Euclidean norm, etc. You can use whichever norm you prefer.  (2 marks)
(c)  Find the vector ρg  and the matrix Yg (q) for the 2-DOF robot example such that the gravity vector g(q) can be expressed as
g(q) = Yg (q)ρg                                                                                              (4)
where ρg  is the rg  × 1 vector of robot parameters and Yg (q) is a n × rg  matrix that depends on q (1 mark).
(d)  Using the linearity in parameters property, we can write the robot manipulator dynamical model τ = M(q)¨(q) + C(q, ˙(q))˙(q) + g(q) in the form. of τ = Y (q, ˙(q) , ¨(q))ρ .  Find the constant vector ρ such that it has the minimum possible number of elements (i.e. the dimension of the vector is minimum) and also find the corresponding Y (q, ˙(q) , ¨(q)).  (2 mark)
2.3    Part 3 (10 marks)We have learned two controllers for the regulation problems in Week 5:  PD controller and PD control with gravity compensation. In this part of the assignment, we want to study another variant of the PD control with gravity compensation:


τ = Kp ˜(q) + KdM(q)(t) + g(q)                                                    (5)
where ˜(q)(t) = qd  − q(t), the matrices Kp , Kd  are n-by-n matrices, and the vector qd  is a constant vector.
(a)  Obtain the closed-loop equation of the system in terms of the state variables ˜(q) and  and verify the
origin is a unique equilibrium point.  (2 marks)
(b)  Find conditions on Kp  and Kd  such that the origin is globally asymptotically stable.  You need to write a detailed mathematical stability proof for this part.  (5 marks)
(c)  Simulate the controller in MATLAB and plot the joint position and velocity errors and show they converge to zero.  Use any Kp  and Kd  gains that satisfy the conditions in Part 3(b) and write the gain values in your report.  (1 marks)
(d)  Among the controller in (5) and the following controller,
τ = Kp ˜(q) + Kd (t) + g(q),                                                     (6)
which one is better to control a real robot?  In other words, is there any difference in terms of the controller performance (both steady-state and transient responses)?  (2 marks)









         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
