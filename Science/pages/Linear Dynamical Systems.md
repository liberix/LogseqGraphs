- # What is Linear Dynamical Systems
	- ## Continous-Time Linear Dynamical System
		- Continous-time linear dynamical system (CD LDS) has the form ( _vector differential equation_):
			- $$
			  \frac{dx}{dt} = A(t) x(t) + B(t) u(t), \quad y(t) = C(t)x(t) + D(t)u(t)
			  $$
			- where:
				- $t \in R$ denotes _time_
				- $x(t) \in R^n$ is the _state_ (vector)
				- $u(t) \in R^m$ is the _input_ or _control_
				- $y(t) \in R^p$ is the _output_
					- Left Equation ( $\frac{dx}{dt} =  \cdots$), called **Dynamics Equation**
					- Right Equation ($y(t) = \cdots$), called **Measurement** or **Readout** **Equation**
				- $A(t) \in R^{n \times n}$ called _Dynamic_ Matirx
				- $B(t) \in R^{n \times n}$ called _Input_ Matirx
				- $C(t) \in R^{n \times n}$ called _Output_ or _Sensor_ Matirx
				- $D(t) \in R^{n \times n}$ called _Feedthrough_ Matirx
				-
		- For lighter appearence, equation can be written
			- $$
			  \dot{x}=Ax + Bu, \quad y = Cx + Du
			  $$
		- CT LDS is a first order vector differential equation
		- also called state equations, or 'm-input, n-state, p-output' LDS
		- ### Terminology
			- most linear systems encountered are _time-invariant_: $A$, $B$, $C$, $D$ are constant. i.e. don't depent on $t$
			- When there is no input $u$ (hence, no $B$ or $D$), system is called _autonomous_
			  id:: 61fbcab1-c518-4338-b2ae-bd574338b3c8
			- very often there is no feedthrough, i.e. $D$
			- when $u(t)$ and $y(t)$ are scalar, system is called _single-input, single-output_ (SISO), other wise is called _multi-input, multi-output_, (MIMO)
	- ## DIscrete-Time Linear Dynamical System
		- form:
			- $$
			  x(t +1) = A(t) x(t) + B(t) u(t), y(t) = C(t)x(t) + D(t)u(t)
			  $$
		- where:
			- $t \in Z = \{0, \pm1, \pm2, \cdots\}$, called _period_ or _sample_
			- (vector) signals $x$, $u$, $y$ are _sequences_
			-