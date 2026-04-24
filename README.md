# week-8

#  Experiment: Precision Half-Wave Rectifiers (Inverting & Non-Inverting)

## AIM

To design, simulate, and analyze **inverting** and **non-inverting precision half-wave rectifier circuits** using an op-amp.

---

##  Components Used

* Op-Amp: uA741
* Resistors: R1 = 10kΩ, R2 = 10kΩ
* Diodes: 1N4148 (D1, D2)
* Power Supply: ±13V

---

##  Input Signal

Vin = SINE(0 0.5 1k)

* Peak-to-Peak Voltage = 1V
* Peak Voltage = 0.5V

---

#  PART A: Inverting Precision Half-Wave Rectifier

##  Design

Gain:
Av = -R2 / R1 = -1

---

##  Transfer Function

Vout = 0        for Vin > 0
Vout = -Vin     for Vin < 0

---

##  Working

###  Positive Half Cycle (Vin > 0)

* Op-amp output swings negative
* D1 → ON, D2 → OFF
* No output path

 Vout = 0

---

### ➤ Negative Half Cycle (Vin < 0)

* Op-amp output swings positive
* D1 → OFF, D2 → ON
* Acts as inverting amplifier

 Vout = -Vin

---

##  Output

<img width="1600" height="812" alt="WhatsApp Image 2026-04-24 at 3 09 43 PM" src="https://github.com/user-attachments/assets/c3595519-a18d-43cc-bcb1-10750c4ee095" />

* Positive input → blocked
* Negative input → inverted to positive

---

#  PART B: Non-Inverting Precision Half-Wave Rectifier

##  Design

Voltage follower configuration during conduction

---

##  Transfer Function

Vout = Vin      for Vin > 0
Vout = 0        for Vin < 0

---

##  Working

###  Positive Half Cycle (Vin > 0)

* Diode ON
* Feedback active
* Output follows input

 Vout = Vin

---

###  Negative Half Cycle (Vin < 0)

* Diode OFF
* Feedback breaks

 Vout = 0

---

##  Output

* Positive input → passed as it is
* Negative input → blocked

---

#  Simulation Setup (LTspice)

## Transient Analysis

.tran 0 10ms

## DC Sweep (Transfer Characteristics)

.dc V1 -0.5 0.5 0.01

---

#  Observations

* Small spikes near zero crossing due to:

  * Op-amp slew rate limitation
  * Diode switching delay
* uA741 is slow → causes minor distortion

---

#  Comparison

| Feature         | Inverting Rectifier | Non-Inverting Rectifier |
| --------------- | ------------------- | ----------------------- |
| Input processed | Negative half       | Positive half           |
| Output polarity | Positive (inverted) | Same as input           |
| Gain            | -1                  | +1                      |
| Complexity      | Moderate            | Simple                  |

---

#  Conclusion

* Precision rectifiers eliminate diode threshold error
* Enable accurate rectification of low-voltage signals
* Both configurations are useful depending on required output polarity

---

#  Applications

* Signal detection
* AC to DC conversion (low voltage)
* Instrumentation systems
* Analog signal processing
