# Tele-Manipulation-Using-Impedance-Control

**Overview**

This Arduino project implements an impedance-controlled dual motor system with force feedback. The system uses rotary encoders for position tracking and a load cell (HX711) for force measurement, allowing for compliant motion that can adapt to external forces.

**Hardware Requirements**

    •	Arduino Uno
    •	Two DC motors with encoders
    •	Motor driver(s) compatible with PWM, direction, and brake control
    •	HX711 load cell amplifier
    •	Load cell/force sensor
    
**Pin Connections**

**Motor A**

    •	PWM: Pin 5
    •	Direction: Pin 4
    •	Brake: Pin 12
    •	Encoder A: Pin 2 (INT0)
    •	Encoder B: Pin 3 (INT1)

**Motor B**

    •	PWM: Pin 11
    •	Direction: Pin 8
    •	Brake: Pin 13
    •	Encoder A: Pin 6
    •	Encoder B: Pin 7

**Load Cell (HX711)**

    •	DOUT: Pin 9
    •	SCK: Pin 10
    
**How It Works**

1.	The user inputs a target angle via serial console
2.	The system moves to the target angle while measuring force
3.	External forces modify the target position according to the virtual spring constant
4.	After reaching the target, the system automatically returns to the home position

**Configuration Parameters**

    •	COUNTS_PER_REV: Encoder resolution (84,240 counts/revolution)
    •	MOTOR_SPEED: Maximum PWM value (200)
    •	MIN_PWM: Minimum PWM to overcome stiction (50)
    •	K_impedance: Virtual spring stiffness (50.0)
    •	Kp_position: Proportional gain for position control (2.0)
    •	ANGLE_TOLERANCE: Positioning tolerance in degrees (2.0)

**Usage**

    1.	Upload the code to your Arduino
    2.	Open the Serial Monitor at 9600 baud
    3.	Enter a positive angle value (in degrees)
    4.	The system will move to the target angle with impedance control
    5.	Apply external forces to see the compliant behavior
    6.	The system will return to home position after reaching the target

**Serial Output**

The system outputs real-time data including:

        •	Current angle
        •	Measured force 
        •	Position adjustment due to force (Δx)
        •	Motor PWM value

