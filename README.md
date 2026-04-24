# Week-8 Experiment

## AIM

To design, simulate, and analyze **inverting** and **non-inverting half-wave rectifier circuits** using an operational amplifier.

---

## COMPONENTS USED

* **Op-Amp:** uA741
* **Resistors:** R1 = 10kΩ, R2 = 10kΩ
* **Diodes:** 1N4148 (D1, D2)
* **Power Supply:** +13V, −13V

---

## INPUT SIGNAL

* Vin = SINE(0 0.5 1K)
* Peak Voltage = 0.5V
* Frequency = 1kHz

---

## THEORY

A **precision rectifier** eliminates the error caused by the diode forward voltage drop (~0.7V).
By placing diodes in the **feedback path of an op-amp**, the circuit compensates for this drop.

This allows accurate rectification of **very small signals (mV range)**.

---

# PART A: INVERTING PRECISION HALF-WAVE RECTIFIER

## DESIGN

The circuit behaves as an **inverting amplifier** during conduction.

---

## CALCULATION

Gain:

Av= -R2/R1 = -10/10 = -1

---

## TRANSFER FUNCTION.

Vout = 0,when Vin > 0
Vout = -Vin, when Vin < 0
---

## WORKING

### Positive Half Cycle ($V_{in} > 0$)

* Op-amp output swings **negative**
* **D1 conducts**, **D2 is OFF**
* Feedback path is inactive for output node

Output:
Vout = 0

*(Op-amp saturates internally, but output is blocked by diode)*

<img width="1600" height="817" alt="Inverting Circuit" src="https://github.com/user-attachments/assets/5e7f1aac-72bb-4c54-b943-b5b34b23557f" />

---

### Negative Half Cycle ($V_{in} < 0$)

* Op-amp output swings **positive**
* **D2 conducts**, **D1 is OFF**
* Feedback path is active

Output:
Vout = -Vin

---

## RESULT

* Positive half cycle is **blocked**
* Negative half cycle is **inverted to positive**

---

# PART B: NON-INVERTING PRECISION HALF-WAVE RECTIFIER

## DESIGN

The circuit behaves as a **voltage follower** during conduction.

---

## CALCULATION

Av=+1

---

## TRANSFER FUNCTION

$$
V_{out} =
\begin{cases}
V_{in}, & V_{in} > 0 \\
0, & V_{in} < 0
\end{cases}
$$

---

## WORKING

### Positive Half Cycle ($V_{in} > 0$)

* Diode is **ON**
* Feedback path is active
* Op-amp operates in closed loop

Output:
Vout = Vin

<img width="1600" height="815" alt="Non-Inverting Circuit" src="https://github.com/user-attachments/assets/09cf0c65-e207-436e-adb9-56319e9b4e79" />

---

### Negative Half Cycle ($V_{in} < 0$)

* Diode is **OFF**
* Feedback path is broken

Output:
Vout = 0

---

## RESULT

* Positive half cycle passes **unchanged**
* Negative half cycle is **blocked**

---

## SIMULATION SETUP (LTspice)

* Transient Analysis:
  `.tran 0 10ms`

* DC Sweep:
  `.dc V1 -0.5 0.5 0.01`

---

## OBSERVATIONS

* Output waveform matches theoretical expectation
* Small distortion near zero crossing observed

### Reasons:

* Limited slew rate of uA741 (~0.5 V/µs)
* Finite gain and bandwidth
* Diode switching delay

---

## JUSTIFICATION

The op-amp compensates for the diode forward voltage drop, enabling accurate rectification of low-voltage signals.
The output closely follows ideal rectifier behavior.

---

## COMPARISON

| Feature            | Inverting Rectifier | Non-Inverting Rectifier |
| ------------------ | ------------------- | ----------------------- |
| Input processed    | Negative half       | Positive half           |
| Output polarity    | Inverted (+)        | Same as input           |
| Gain               | -1                  | +1                      |
| Circuit complexity | Moderate            | Simple                  |

---

## APPLICATIONS

* Signal detection
* Low-voltage AC to DC conversion
* Instrumentation systems
* Analog signal processing

---

## CONCLUSION

The inverting and non-inverting precision half-wave rectifiers were successfully designed and simulated using LTspice.
The circuits eliminate diode threshold error and accurately rectify low-amplitude signals.
The choice of configuration depends on the required output polarity.

---
