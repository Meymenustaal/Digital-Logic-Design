# 🔢 Hardware Logic Design: Asynchronous MOD-9 Counter

## 📌 Project Overview
This project demonstrates the design and physical implementation of a digital state machine using entirely discrete TTL logic components, without relying on any microcontroller or software.
Based on the classic sequential logic design methodologies outlined in **M. Morris Mano's "Digital Design"** book,
the system operates as an asynchronous up counter that counts sequentially from 0 to 8 and resets to zero.

## ⚙️ Hardware Architecture and Components
The system is built on a breadboard using entirely discrete ICs and requires precise power regulation and independent clock generation:
* **Power Regulation:** LM7805 Linear Voltage Regulator (reduces a 9V battery supply to a stable 5V TTL level).

* **Clock Generation:** NE555 Timer IC configured in astable mode.

* **Logic Core:** 2x SN74LS76N (Dual JK Flip-Flop), configured in toggle mode ( $J=K=1$ ).

* **Reset Logic:** SN74LS00 (Quad NAND Gate) to detect the '1001' (9) state and trigger an asynchronous reset.

## 🧠 System Dynamics and Clock Calculation
Instead of using software delays, the system timing is driven by the NE555 timer.
The resistor-capacitor (RC) network is mathematically calculated to generate a 1 Hz clock pulse to provide visible state transitions on the LEDs.

**Stable Frequency Calculation:**
`f = 1.44 / ((R1 + 2*R2) * C)`
`f = 1.44 / ((10kΩ + 2*68kΩ) * 10µF) ≈ 0.99 Hz (1 Pulse per Second)`

Four JK flip-flops are connected asynchronously in series. The output of each flip-flop drives the clock input of the next. 
When the system reaches the binary state `1001`, the NAND gate immediately forces the active low CLR pins to ground and 
instantly resets the counter to `0000` to maintain the MOD-9 constraint.


## 📷 Media
<img width="1337" height="522" alt="image" src="https://github.com/user-attachments/assets/b8539a16-6803-4055-81b9-ab3db68354d9" />


<img width="600" height="818" alt="image" src="https://github.com/user-attachments/assets/efefda05-cbe9-4acb-8e0a-3c7dc68441db" />
