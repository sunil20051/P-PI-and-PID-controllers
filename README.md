# Analysis of P, PI and PID Controllers using MATLAB
## Aim:
To analyse the effect of P, PI and PID controllers for the system having open loop transfer function, G(S)=1/(S^2+10S+20) using MATLAB. 
## Apparatus Required:
Computer with MATLAB software

## Theory:
	A controller is a device introduced in the system to modify the error signal and to produce a control signal. 
	The way the controller produces the control signal is called the control action.

Consider the following unity feedback system,
 <img width="823" height="281" alt="image" src="https://github.com/user-attachments/assets/36e49512-cf47-4fec-b00c-f79dc0af1c5f" />

### Proportional (P) Controller:
The proportional controller produces an output, which is proportional to error signal.<br>
u(t)∝e(t) <br>
⇒u(t)=Kpe(t) <br>
Apply Laplace transform on both the sides - <br>
U(s)=KpE(s) <br>
U(s)/E(s)=Kp <br>
Therefore, the transfer function of the proportional controller is Kp.

### Proportional Integral (PI) Controller:
The proportional integral controller produces an output, which is the combination of outputs of the proportional and integral controllers. <br>
u(t)=Kp e(t)+Ki ∫e(t)dt <br>
Apply Laplace transform on both sides - <br>
U(s)=(Kp+Ki/s)E(s) <br>
U(s)/E(s)=Kp+Ki/s <br>
Therefore, the transfer function of proportional integral controller is Kp+Kis. <br>

### Proportional Integral Derivative (PID) Controller:
The proportional integral derivative controller produces an output, which is the combination of the outputs of proportional, integral and derivative controllers. <br>
u(t)=Kp e(t)+Ki ∫e(t)dt+ Kd (de(t)/dt) <br>
Apply Laplace transform on both sides - <br>
U(s)=(Kp+Ki/s+Kds)E(s) <br>
U(s)/E(s)=Kp+Ki/s+Kd s <br>
Therefore, the transfer function of the proportional integral derivative controller is Kp+Ki/s+Kd s

### Characteristics of Kp, Ki and Kd terms:

Increasing the proportional gain ( ) has the effect of proportionally increasing the control signal for the same level of error. The fact that the controller will "push" harder for a given level of error tends to cause the closed-loop system to react more quickly, but also to overshoot more. Another effect of increasing   is that it tends to reduce, but not eliminate, the steady-state error.
The addition of a derivative term to the controller ( ) adds the ability of the controller to "anticipate" error. With derivative control, the control signal can become large if the error begins sloping upward, even while the magnitude of the error is still relatively small. This anticipation tends to add damping to the system, thereby decreasing overshoot. The addition of a derivative term, however, has no effect on the steady-state error.
The addition of an integral term to the controller ( ) tends to help reduce steady-state error. If there is a persistent, steady error, the integrator builds and builds, thereby increasing the control signal and driving the error down. 
 


## Procedure:
	Open MATLAB software
	Open a new script file.
	Type the program.
	Save and Execute the program.
	Determine the steady state error and analyse the controllers.
## Program: 
### Without Controller (Open loop System)
num=[1];<br>
den=[1 10 20];<br>
sys=tf(num,den)<br>
step(sys)<br>

### With P-Controller
num=[1];<br>
den=[1 10 20];<br>
sys=tf(num,den)<br>
Kp=300;<br>
C=pid(Kp);<br>
T=feedback(C*sys,1);<br>
step(T)<br>

### With PI Controller
num=[1];<br>
den=[1 10 20];<br>
sys=tf(num,den)<br>
Kp=30;<br>
Ki=70;<br>
C=pid(Kp,Ki);<br>
T=feedback(C*sys,1);<br>
step(T)<br>


### With PID Controller
num=[1];<br>
den=[1 10 20];<br>
sys=tf(num,den)<br>
Kp=350;<br>
Ki=300;<br>
Kd=50;<br>
C=pid(Kp,Ki,Kd);<br>
T=feedback(C*sys,1);<br>
step(T)<br>

## Output: 
### Without Controller (Open loop System)

<img width="1914" height="1137" alt="image" src="https://github.com/user-attachments/assets/adaa085b-391a-4518-80d7-76dba2147106" />


### With P-Controller
<img width="1917" height="1127" alt="image" src="https://github.com/user-attachments/assets/d6347461-3cd7-4947-b62a-eb11c447d4a6" />



### With PI Controller
<img width="1916" height="1140" alt="image" src="https://github.com/user-attachments/assets/a0dfd12f-9737-49bb-8314-7665a56becad" />


### With PID Controller
<img width="1915" height="1136" alt="image" src="https://github.com/user-attachments/assets/c4c70e5b-aeb1-4105-99aa-d336c703b2d0" />



## Result:
Thus the P, PI and PID controllers for the given system was analysed and the following conclusions were arrived using MATLAB. <br>
### With-out controller 
Delay time =   0.458s      <br>
Rise time =  1.56s           <br>
Peak time =    0.999s     <br>
Settling time =  1.96s          <br>
Steady State Error =   0     <br>
### With P Controller 
Delay time =   0.0887s      <br>
Rise time =    0.16s         <br>
Peak time =     0.19s      <br>
Settling time =   1.1s         <br>
Steady State Error =   0.1     <br>
### With PI Controller 
Delay time =    0.303s     <br>
Rise time =     0.649s        <br>
Peak time =     0.82s      <br>
Settling time =     1.87s       <br>
Steady State Error =  0.87      <br>
### With PID Controller 
Delay time =  0.0243s       <br>
Rise time =   0.0615s          <br>
Peak time =   1.04s        <br>
Settling time =   0.882s         <br>
Steady State Error = 0.018       <br>
