# 📘 24EECE2001 — Master Reference README
### Units 1 & 2 | Semiconductors & Diodes

> **How to use this file**
> - [1. Constants You Must Memorize](#1-constants-you-must-memorize)
> - [2. Formula Sheet](#2-formula-sheet)
> - [3. Derivations](#3-derivations)
> - [4. Long Answer Theory](#4-long-answer-theory)
> - [5. Short Answer Q&A](#5-short-answer-qa)

---

## 1. Constants You Must Memorize

| Symbol | Name | Exact Value | SI Units |
|---|---|---|---|
| $q$ | Elementary Charge | $1.602 \times 10^{-19}$ | C |
| $k$ | Boltzmann Constant | $1.38 \times 10^{-23}$ | J/K |
| $k$ | Boltzmann Constant (eV) | $8.62 \times 10^{-5}$ | eV/K |
| $V_T$ | Thermal Voltage (at 300 K) | $25.9$ | mV |
| $\epsilon_0$ | Permittivity of Free Space | $8.854 \times 10^{-14}$ | F/cm |
| $\epsilon_{si}$ | Permittivity of Silicon | $1.04 \times 10^{-12}$ | F/cm |
| $n_i$ | Intrinsic Carrier Concentration (Si, 300 K) | $1.5 \times 10^{10}$ | cm⁻³ |
| $E_g$ | Bandgap Energy of Silicon (300 K) | $1.12$ | eV |

---

## 2. Formula Sheet

### 2.1 Carrier Concentration & Transport

| Formula Name | Equation | Variables | Units |
|---|---|---|---|
| Mass-Action Law | $np = n_i^2$ | $n$: electron conc., $p$: hole conc., $n_i$: intrinsic conc. | cm⁻³ |
| Charge Neutrality | $p + N_D = n + N_A$ | $N_D$: donor conc., $N_A$: acceptor conc. | cm⁻³ |
| Conductivity | $\sigma = q(n\mu_n + p\mu_p)$ | $\mu_n, \mu_p$: electron/hole mobility | S/cm |
| Drift Current Density | $J_{drift} = q(n\mu_n + p\mu_p)E$ | $E$: applied electric field | A/cm² |
| Diffusion Current Density | $J_{diff} = qD_n \dfrac{dn}{dx} - qD_p \dfrac{dp}{dx}$ | $D_n, D_p$: diffusion coefficients | A/cm² |
| Einstein Relation | $\dfrac{D_n}{\mu_n} = \dfrac{D_p}{\mu_p} = V_T$ | $V_T = \dfrac{kT}{q}$ (thermal voltage) | V |

### 2.2 PN Junction & Ideal Diode

| Formula Name | Equation | Variables | Units |
|---|---|---|---|
| Built-in Potential | $V_0 = V_T \ln\!\left(\dfrac{N_A N_D}{n_i^2}\right)$ | $N_A$: acceptor conc., $N_D$: donor conc. | V |
| Depletion Width | $W = \sqrt{\dfrac{2\epsilon_{si}}{q}\left(\dfrac{1}{N_A} + \dfrac{1}{N_D}\right)V_0}$ | $\epsilon_{si}$: permittivity of Si, $V_0$: barrier potential | cm |
| Shockley Diode Equation | $I = I_S\left(e^{V/nV_T} - 1\right)$ | $I_S$: saturation current, $n$: ideality factor (1 or 2) | A |
| Dynamic Resistance | $r_d = \dfrac{nV_T}{I_Q}$ | $I_Q$: quiescent forward current | Ω |

### 2.3 Rectifiers & Filters

| Formula Name | Equation | Variables | Units |
|---|---|---|---|
| HW Rectifier $V_{dc}$ | $V_{dc} = \dfrac{V_m}{\pi}$ | $V_m$: peak secondary voltage | V |
| FW Rectifier $V_{dc}$ | $V_{dc} = \dfrac{2V_m}{\pi}$ | $V_m$: peak secondary voltage | V |
| Ripple Factor ($\gamma$) | $\gamma = \sqrt{\left(\dfrac{V_{rms}}{V_{dc}}\right)^2 - 1}$ | $V_{rms}$: RMS voltage of output | Unitless |
| FW Filtered Ripple | $V_r = \dfrac{V_m}{2fCR}$ | $f$: frequency, $C$: capacitance, $R$: load | V (peak-to-peak) |

---

## 3. Derivations

### 3.1 Built-in Potential ($V_0$) of a PN Junction

**Assumptions**
- The PN junction is in thermal equilibrium (no applied voltage, open circuit).
- Net current across the junction is zero — electron drift current exactly cancels electron diffusion current (and likewise for holes).

**Steps**

1. Zero net electron current density ($J_n = 0$):

$$J_{n,drift} + J_{n,diff} = 0 \quad\Rightarrow\quad q\mu_n n E + qD_n \frac{dn}{dx} = 0$$

2. Rearrange to relate field and concentration gradient:

$$\mu_n n E = -D_n \frac{dn}{dx}$$

3. Substitute $E = -\dfrac{dV}{dx}$:

$$\mu_n n \left(-\frac{dV}{dx}\right) = -D_n \frac{dn}{dx}$$

4. Apply the Einstein Relation ($D_n = \mu_n V_T$) and simplify:

$$-\mu_n n \frac{dV}{dx} = -\mu_n V_T \frac{dn}{dx} \quad\Rightarrow\quad dV = V_T \frac{dn}{n}$$

5. Integrate across the depletion region — potential from $0$ (p-side) to $V_0$ (n-side); electron concentration from $n_{p0}$ to $n_{n0}$:

$$\int_{0}^{V_0} dV = V_T \int_{n_{p0}}^{n_{n0}} \frac{1}{n}\, dn \quad\Rightarrow\quad V_0 = V_T \ln\!\left(\frac{n_{n0}}{n_{p0}}\right)$$

6. Substitute majority/minority concentrations — with full ionization, $n_{n0} \approx N_D$, and by mass-action law, $n_{p0} \approx n_i^2 / N_A$:

$$V_0 = V_T \ln\!\left(\frac{N_D}{n_i^2 / N_A}\right)$$

**Result**

$$\boxed{V_0 = V_T \ln\!\left(\frac{N_A N_D}{n_i^2}\right)}$$

### 3.2 Ripple Factor of a Full-Wave Rectifier

**Assumptions**
- Input is a pure sinusoid, $v(t) = V_m \sin(\omega t)$.
- Diodes are ideal.

**Steps**

1. DC (average) value of the full-wave output over one half-cycle ($0$ to $\pi$):

$$V_{dc} = \frac{1}{\pi} \int_{0}^{\pi} V_m \sin(\theta)\, d\theta = \frac{V_m}{\pi}\big[-\cos(\theta)\big]_0^\pi = \frac{2V_m}{\pi}$$

2. RMS value over the same period:

$$V_{rms} = \sqrt{\frac{1}{\pi} \int_{0}^{\pi} V_m^2 \sin^2(\theta)\, d\theta} = V_m\sqrt{\frac{1}{\pi}\int_0^\pi \frac{1-\cos(2\theta)}{2}\,d\theta} = \frac{V_m}{\sqrt{2}}$$

3. Ripple factor $\gamma$ is the ratio of the AC component's RMS value to the DC component. Using $V_{rms}^2 = V_{dc}^2 + V_{ac,rms}^2$:

$$\gamma = \frac{V_{ac,rms}}{V_{dc}} = \sqrt{\left(\frac{V_{rms}}{V_{dc}}\right)^2 - 1}$$

4. Substitute the derived $V_{rms}$ and $V_{dc}$:

$$\gamma = \sqrt{\left(\frac{V_m/\sqrt{2}}{2V_m/\pi}\right)^2 - 1} = \sqrt{\frac{\pi^2}{8} - 1}$$

**Result**

$$\boxed{\gamma \approx 0.482 \ \text{(48.2\%)}}$$

---

## 4. Long Answer Theory

### Q: Explain energy band theory. How does it distinguish insulators, intrinsic semiconductors, and extrinsic semiconductors?

**Formation of bands** — When isolated atoms form a crystal lattice, the Pauli Exclusion Principle forbids any two electrons from sharing the same quantum state. Overlapping atomic orbitals split into tightly spaced energy levels, forming continuous **bands**: the **Valence Band** (highest band, fully occupied at 0 K) and the **Conduction Band** (next band up, empty at 0 K), separated by the **Bandgap Energy ($E_g$)**.

- **Insulators** — Very large bandgap ($E_g > 5$ eV). At room temperature, thermal energy ($kT \approx 0.0259$ eV) is far too small to excite electrons into the conduction band, so the valence band stays full and the conduction band stays empty — conductivity is essentially zero.
- **Intrinsic Semiconductors** — Moderate bandgap (Si $\approx 1.12$ eV). At 0 K they behave as insulators; at room temperature thermal energy breaks some covalent bonds, exciting electrons into the conduction band and leaving holes in the valence band, with $n = p = n_i$.
- **Extrinsic Semiconductors** — Conductivity is boosted by intentional doping:
  - **N-type**: doped with Group V atoms (e.g., phosphorus). The extra valence electron is loosely bound and sits at a donor level just below the conduction band, donating electrons easily — electrons are the majority carrier.
  - **P-type**: doped with Group III atoms (e.g., boron). The missing bond electron creates an acceptor level just above the valence band, which readily accepts electrons and leaves holes — holes are the majority carrier.

### Q: Contrast drift and diffusion current. What drives each?

**Drift Current**
- **Mechanism**: directed carrier motion under an applied external electric field.
- **Physics**: an electric field $E$ accelerates holes along the field and electrons against it; carriers repeatedly collide with the vibrating lattice, settling into a steady average drift velocity, $v_d = \mu E$.
- **Depends on**: carrier concentration, applied field, and mobility ($\mu$).

**Diffusion Current**
- **Mechanism**: carrier motion driven by a concentration gradient, from high to low concentration.
- **Physics**: driven by random thermal (Brownian) motion — no external field is needed. Carriers injected at one point spread out toward a uniform distribution.
- **Depends on**: the spatial gradient of concentration ($dn/dx$ or $dp/dx$) and the diffusion coefficient $D$, which is set by thermal energy.

### Q: Detail the physical mechanisms of Zener vs. Avalanche breakdown in a reverse-biased PN junction.

**Zener Breakdown**
- **Conditions**: heavily doped junctions → very narrow depletion region.
- **Mechanism**: a thin depletion region means even a modest reverse bias (< 5 V) produces an intense field ($E = V/W$), strong enough to pull electrons directly out of covalent bonds via quantum tunneling from the p-side valence band into the n-side conduction band.
- **Characteristic**: **negative** temperature coefficient — breakdown voltage falls as temperature rises.

**Avalanche Breakdown**
- **Conditions**: lightly doped junctions → wide depletion region.
- **Mechanism**: at higher reverse bias (> 5 V), minority carriers crossing the wide depletion region gain enough kinetic energy to collide with lattice atoms, breaking covalent bonds and generating new electron-hole pairs (impact ionization). These new carriers accelerate and collide further, cascading into a large reverse current.
- **Characteristic**: **positive** temperature coefficient — breakdown voltage rises with temperature as increased lattice scattering shortens the carrier mean free path.

### Q: Explain the operating principles of clamping and limiting (clipping) circuits.

**Limiter (Clipper) Circuits**
- **Function**: caps the input signal at a set positive or negative threshold.
- **Operation**: built from resistors and diodes (often with a DC bias source). Once the input exceeds $V_{limit} = V_{bias} + 0.7$ V, the diode turns ON and clamps the output at that level; below threshold the diode is OFF and the signal passes through unchanged.

**Clamper (DC Restorer) Circuits**
- **Function**: shifts the entire AC waveform up or down by a fixed DC level without changing its peak-to-peak shape.
- **Operation**: built from a capacitor, diode, and resistor. During the half-cycle that forward-biases the diode, the capacitor charges to the input peak; once charged, the diode turns OFF. Because the discharge time constant $RC$ is made much larger than the signal period, the capacitor behaves like a DC battery in series with the input, giving $v_{out} = v_{in} \pm V_c$.

---

## 5. Short Answer Q&A

**Q: What is the Fermi Level?**
A: The energy level at which the probability of finding an electron is exactly 50% at thermal equilibrium. In intrinsic semiconductors it lies near the middle of the bandgap.

**Q: Define carrier mobility ($\mu$).**
A: A measure of how easily a carrier (electron or hole) moves through a semiconductor under an electric field; it relates drift velocity to field via $v_d = \mu E$.

**Q: What is the depletion region?**
A: The region near a PN junction depleted of mobile carriers due to diffusion and recombination, leaving behind fixed, charged impurity ions that create a built-in electric field.

**Q: What is thermal voltage ($V_T$)?**
A: The voltage equivalent of a particle's thermal energy at a given temperature, $V_T = kT/q$. At room temperature (300 K) it is approximately 25.9 mV.

**Q: What is the barrier (built-in) potential, $V_0$?**
A: The potential difference across the depletion region at thermal equilibrium; it opposes further diffusion of majority carriers across the junction.

**Q: Why does a capacitor filter reduce ripple in a rectifier circuit?**
A: The capacitor charges to the peak of the rectified voltage, then discharges slowly through the load as the rectified wave dips below the peak. With a large $RC$ time constant, the output stays close to the peak, smoothing out the sharp drops of the rectified sine wave.

---

*End of 24EECE2001 Master Reference README — Units 1 & 2, Complete*
