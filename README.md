# voltage-mode-buck-compensation
Master's thesis project: A 25V to 20V/5A synchronous DC-DC buck converter (LM5145) with feedback loop compensation analysis.

# Comparative Analysis of Feedback Loop Compensation Networks in a Voltage-Mode DC/DC Converter

## Objective and Scope
The objective of this project was to design, physically build, and commission a custom synchronous step-down (Buck) converter operating in Voltage-Mode Control.

Based on the designed and assembled hardware, the impact and effectiveness of three types of analog compensation networks (Type I, Type II, and Type III) on the stability and dynamic response of the power supply were verified. The project is a comprehensive engineering study that includes:

* Theoretical small-signal modeling and parameter calculations.
* Selection of electronic components, taking into account their parasitic phenomena in real-world operating conditions.
* Custom engineering design of the printed circuit board (PCB).
* Practical laboratory measurements of closed-loop characteristics on the constructed test stand.

---

## Converter Design Specification

| Parameter | Value | Additional Information |
| :--- | :--- | :--- |
| **Controller** | Texas Instruments LM5145 | Synchronous controller with external MOSFETs |
| **Input Voltage ($V_{IN}$)** | 25 V (nominal) | UVLO thresholds: turn-on 24.14 V, turn-off 23.14 V |
| **Output Voltage ($V_{OUT}$)** | 20 V | - |
| **Output Current ($I_{OUT}$)** | 5 A | Maximum output power $P_{OUT}$ = 100 W |
| **Switching Frequency ($f_{sw}$)**| 300 kHz | - |
| **Inductor ($L$)** | 8.2 µH | - |
| **Output Capacitance ($C_{OUT}$)** | 114.335 µF | Compensated total value including a 68 µF electrolytic capacitor and a 46.335 µF bank of MLCC ceramic capacitors subjected to the DC Bias effect. |

---

## Analysis of Compensation Networks

As part of the project, three compensation topologies in the feedback loop were implemented and subjected to a practical comparative analysis:

* **Type I** 
* **Type II** 
* **Type III**

For each circuit, frequency responses were determined via simulation, and the impact of the applied structure on the stability and dynamic response of the converter was analyzed, avoiding solutions that limit the system's bandwidth.

---

## Key Engineering Solutions

During the hardware design process, the real physical phenomena of electronic components were taken into account:
* **Accounting for the DC Bias effect in ceramic capacitors:** The parameters of the output MLCC bank were selected with particular emphasis on their capacitance degradation under a constant 20 V bias voltage. The actual drop from 22 µF to 15.45 µF per MLCC capacitor was calculated, which was directly included in the total output capacitance balance.
* **Minimization of dead-time losses:** An external Schottky diode (Vishay VSSAF5N50) was connected in parallel with the low-side MOSFET (AON6234), which reduces the losses on the transistor's body diode and limits current spikes.
* **Signal injection for AC measurements:** A 20-ohm injection resistor was placed in the circuit, allowing a small-signal injection via an isolation transformer to plot Bode diagrams.

---

## Summary and Conclusions

The project and laboratory measurements conducted on the test stand proved that the Type III compensator is the optimal solution for the analyzed converter. The comparative analysis demonstrated the limitations of simpler structures (Type I and II), highlighting the advantages of Type III, which directly allowed for:

* Effective compensation of the LC filter's double pole, which was crucial for stability in the selected control mode.
* Setting the target crossover frequency ($f_c$) at 60 kHz while maintaining a safe phase margin ($\phi_m$) of 60°.
* Achieving the shortest settling time after a load step transient.
* Significant minimization of output voltage sag and reduction of overshoot, which directly translates into higher power supply quality.

## Repository Structure

* **`docs/`** – Full project documentation (Master's thesis PDF).
* **`hardware/`** – Source files of the project from Altium Designer (`.SchDoc`, `.PcbDoc`, and Gerber files).
* **`measurements/`** – Test results of the real circuit (captured oscillograms, load step responses for each compensation type).

## Author
* **Mikołaj Siewierski, MSc**