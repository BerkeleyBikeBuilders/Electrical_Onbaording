# Section 4: PWM Driver Design Concepts and Schematic

> Make sure you finish Section 3's practice section before starting!
> Also make sure you have watched this [video](https://www.youtube.com/watch?v=UPTU6nYSaMo&t=860s) before starting on this section!

For this project you will be designing your own PCB: the motor driver for the Bike Builders e-bike. A potentiometer acts as the throttle, and it controls the speed of the e-bike motor through a 555 timer and PWM. Here are the project requirements:
- A way to power and control an LED (the schematic you made in the previous section).
- A potentiometer that controls the speed of the e-bike motor through a 555 timer and PWM.
- The board will be powered from an external 12V supply through a connector.

However, there are a few concepts you should understand first.

## Pulse Width Modulation

PWM (Pulse Width Modulation) is a technique used to control the power delivered to electronic devices. It works by switching a signal between high (on) and low (off) states at a fast rate, which lets us average the power. The duty cycle (the percentage of time the signal is high) determines the effective average power. For example, PWM can control the brightness of an LED or the speed of the e-bike motor.

How it works:
- A higher duty cycle (e.g., 75% high, 25% low) delivers more power.
- A lower duty cycle (e.g., 25% high, 75% low) delivers less power.
- This is efficient because the switching circuit dissipates very little power, since it is either fully on or fully off.

## 555 Timer
The 555 timer is a versatile integrated circuit used for timing, pulse generation, and oscillator applications. For example, 555 timers can generate clock pulses for circuits. The key skill to use here is abstraction from Section 2! You can check out the datasheet if you are interested.

How to use it:
- Internally, it uses voltage comparators, a flip-flop, and a discharge transistor.
- By configuring external resistors and capacitors, you set the timing intervals.

## RC Circuit
An RC circuit consists of a resistor (R) and a capacitor (C). It can be used for filtering and timing. In our case, we use it as a timer.

How it works:
- The capacitor charges and discharges through the resistor, with the rate determined by the time constant.
- In a low-pass filter, it allows low frequencies to pass and blocks high frequencies.
- In a high-pass filter, it allows high frequencies to pass and blocks low frequencies.

### Decoupling Capacitors
Decoupling capacitors are filters used to stabilize voltage in electronic circuits. For example, decoupling capacitors reduce noise in microcontroller circuits.

How it works:
- They are placed near integrated circuits (ICs) to filter out noise and provide instantaneous current during transient demands.
- When the supply voltage fluctuates, the capacitor absorbs or supplies charge, maintaining a stable voltage.

## MOSFETs
A MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor) is a type of transistor used as a switch or amplifier in electronic circuits. For example, MOSFETs are used for switching power to a motor or amplifying audio signals. In our case, we use it as a switch for the e-bike motor to create our on and off PWM signal.

How it works:
- The MOSFET has three terminals: Gate, Drain, and Source.
- Applying voltage to the Gate creates an electric field, controlling the flow of current between the Drain and the Source.

There are two main types:
- N-channel: Current flows when the gate voltage is positive.
- P-channel: Current flows when the gate voltage is negative.

MOSFET gate resistors are used to:
- Limit the current into the MOSFET's gate when switching.
- Prevent damage to the MOSFET from high inrush current and excessive ringing caused by fast switching and parasitic inductance.
- Lead to smoother operation in PWM-controlled circuits.

# Checkpoint and Deliverables (IMPORTANT!)
- In the same file where you made your single LED circuit, you will build your PWM driver (the e-bike motor driver) circuit.
- You will build the same functional circuit as the image below (it does not have to be a carbon copy!).
- Make sure to run the ERC checker (top toolbar) to make sure KiCad is happy with your schematic!
- Take a screenshot of your circuit (both the LED and the PWM driver) and the ERC checker, and show a lab staff member to move on to the next section once your circuit is approved!
- Ask for help if you need it!

Lab Staff to reach out to: (add your lab staff here)

(Please note in the image below, the LED circuit on the left should be the LED circuit you made in Section 3.)

![Onboarding Lab Schematic](https://github.com/user-attachments/assets/a69d805a-5a81-40b7-b31b-0eb244053f46)
