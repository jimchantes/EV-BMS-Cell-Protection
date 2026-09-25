# EV Li-Ion Battery Cell Protection Circuit (Window Comparator)

An overvoltage and undervoltage monitoring circuit (BMS/AMS aspect) designed for a Formula Student Electric Vehicle (EV). The circuit monitors a single lithium-ion cell, ensuring it stays within the safe operating window of **3.0V to 4.2V**. If the cell voltage violates these parameters, the system triggers a **0V Fault Signal** to open the safety shutdowns.

## Project Structure
* `/Simulation`: LTspice circuit schematic and transient/DC sweep simulation files.
* `/Hardware`: KiCad schematic blueprints, footprint assignments, and PCB layout routing.

## Technical Specifications
* **Overvoltage Threshold (OV):** 4.2V
* **Undervoltage Threshold (UV):** 3.0V
* **Logic Output:** 5V (Safe Condition) / 0V (Fault Condition)
* **Threshold Reference:** Precision resistive ladder divider network (1.6kΩ / 2.4kΩ / 6.0kΩ) connected to a regulated 5V VCC line.

## Simulation & Validation (LTspice)
The circuit behavior was validated using LTspice. To bypass idealized push-pull macro-model contention, the window comparator output was isolated utilizing a diode network pulled up to a stable 5V rail.

<img width="1207" height="832" alt="image" src="https://github.com/user-attachments/assets/d53eb0af-7a0f-49b6-baf4-43c88880efb2" />
<img width="1913" height="431" alt="image" src="https://github.com/user-attachments/assets/dc6132d7-24bf-4ffb-b42c-f62856c17f08" />


*Result:* The simulation confirms a sharp, deterministic transition to 0V whenever the swept input voltage falls below 3.0V or exceeds 4.2V.

## Hardware Design (KiCad PCB)
The validated schematic was fully routed into a functional, single-layer Through-Hole (THT) PCB optimized for easy benchtop prototyping and verification.

* **Core IC:** LM393 Dual Differential Comparator (DIP-8 package)
* **Routing:** 45-degree trace angles to minimize EMI and maintain professional manufacturing standards.
* **Connector:** 4-Pin terminal header separating Vin (Cell Monitor), VCC (5V System Power), GND, and the Fault Output.

<img width="442" height="470" alt="image" src="https://github.com/user-attachments/assets/cff9ce7c-39c7-4705-894b-5a29dcd320a2" />
<img width="602" height="567" alt="image" src="https://github.com/user-attachments/assets/2fcbfd81-1b10-4a67-86b2-d6207aba349c" />
