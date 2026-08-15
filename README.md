# 📘 EDC Sessional 1 — Master Reference README
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

### 2.3 Junction Capacitances

| Formula Name | Equation | Variables | Units |
|---|---|---|---|
| Zero-Bias Depletion Cap. | $C_{j0} = A\sqrt{\dfrac{q\,\epsilon_{si}}{2V_0}\left(\dfrac{N_A N_D}{N_A + N_D}\right)}$ | $A$: cross-sectional area, $V_0$: built-in potential | F |
| Depletion Cap. (Reverse) | $C_j = \dfrac{C_{j0}}{\left(1 + \dfrac{V_R}{V_0}\right)^m}$ | $V_R$: reverse bias magnitude, $m$: grading coefficient | F |
| Minority Carrier Transit Time | $\tau_T = \dfrac{L_n^2}{2D_n} + \dfrac{L_p^2}{2D_p}$ | $L$: diffusion length, $D$: diffusion coefficient | s |
| Diffusion Cap. (Forward) | $C_d = \left(\dfrac{\tau_T}{V_T}\right) I_Q$ | $\tau_T$: transit time, $I_Q$: quiescent forward current | F |

### 2.4 Rectifiers & Filters

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

### 3.2 The Ideal Diode Equation (Shockley Equation)

**Assumptions**
The ideal I–V relationship of a PN junction rests on four assumptions:
1. Space-charge regions have abrupt boundaries, and the semiconductor is neutral outside this region.
2. Maxwell–Boltzmann statistics apply to carrier populations.
3. **Low-level injection** holds — majority carrier concentration does not change significantly.
4. Total current ($I$) is constant throughout the entire PN structure.

**Steps**

1. At thermal equilibrium, relate the minority electron concentration on the p-side ($n_{p0}$) to the majority concentration on the n-side ($n_{n0}$) via the built-in potential ($V_{bi}$):

$$n_{p0} = n_{n0} \exp\!\left(-\frac{qV_{bi}}{kT}\right)$$

2. Under forward bias ($V_A$), the barrier voltage becomes $(V_{bi} - V_A)$, so the minority carrier concentration at the depletion-region edge becomes:

$$n_p = n_{n0} \exp\!\left(-\frac{q(V_{bi} - V_A)}{kT}\right) = n_{p0} \exp\!\left(\frac{qV_A}{kT}\right)$$

By the same argument, for holes injected into the n-region:

$$p_n = p_{n0} \exp\!\left(\frac{qV_A}{kT}\right)$$

3. Forward bias drives steady-state injection of excess carriers. The excess hole concentration ($\Delta p_n$) and excess electron concentration ($\Delta n_p$) are:

$$\Delta p_n = p_n\left(\exp\!\left(\frac{qV_A}{kT}\right) - 1\right), \qquad \Delta n_p = n_p\left(\exp\!\left(\frac{qV_A}{kT}\right) - 1\right)$$

4. The hole diffusion current at any point $x_n$ is proportional to the concentration gradient. Using the minority carrier diffusion length ($L_p$) and cross-sectional area ($A$):

$$I_p(x_n) = -qAD_p \frac{d\Delta p(x_n)}{dx_n} = \frac{qAD_p \Delta p_n}{L_p}$$

Evaluated at the boundary ($x_n = 0$):

$$I_p(x_n=0) = \frac{qAD_p p_n}{L_p} \left(\exp\!\left(\frac{qV_A}{kT}\right) - 1\right)$$

By the same argument for electrons at the p-side boundary ($x_p = 0$):

$$I_n(x_p=0) = \frac{qAD_n n_p}{L_n} \left(\exp\!\left(\frac{qV_A}{kT}\right) - 1\right)$$

5. Total diode current is the sum of both diffusion currents evaluated at the space-charge edges:

$$I = I_p(x_n=0) + I_n(x_p=0) = qA \left( \frac{D_p p_n}{L_p} + \frac{D_n n_p}{L_n} \right) \left(\exp\!\left(\frac{qV_A}{kT}\right) - 1\right)$$

6. Group the leading constant term as the Reverse Saturation Current ($I_0$):

$$I_0 = qA \left( \frac{D_p p_n}{L_p} + \frac{D_n n_p}{L_n} \right)$$

**Result**

$$\boxed{I = I_0 \left(\exp\!\left(\frac{qV_A}{kT}\right) - 1\right)}$$

### 3.3 Ripple Factor of a Full-Wave Rectifier

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

**Formation of bands** — Overlapping atomic orbitals in a crystal lattice split into tightly spaced energy levels forming continuous **bands**: the **Valence Band** (highest band, fully occupied at 0 K) and the **Conduction Band** (next band up, empty at 0 K), separated by the **Bandgap Energy ($E_g$)**.

- **Insulators** — Very large bandgap ($E_g > 5$ eV). At room temperature, thermal energy ($kT$) is far too small to excite electrons into the conduction band, so conductivity is essentially zero.
- **Intrinsic Semiconductors** — Moderate bandgap (Si $\approx 1.12$ eV). At 0 K they behave as insulators; at room temperature thermal energy breaks covalent bonds, exciting electrons into the conduction band and leaving holes behind, with $n = p = n_i$.
- **Extrinsic Semiconductors** — Conductivity is boosted by intentional doping:
  - **N-type**: doped with Group V atoms (e.g., phosphorus). Introduces a donor level just below the conduction band — electrons are the majority carrier.
  - **P-type**: doped with Group III atoms (e.g., boron). Creates an acceptor level just above the valence band — holes are the majority carrier.

### Q: Contrast drift and diffusion current. What drives each?

**Drift Current**
- **Mechanism**: directed carrier motion under an applied external electric field.
- **Physics**: holes accelerate along the field, electrons against it; constant collisions with the lattice yield a steady average drift velocity, $v_d = \mu E$.

**Diffusion Current**
- **Mechanism**: carrier motion driven by a concentration gradient, from high to low concentration.
- **Physics**: driven purely by random thermal motion — no external field is required.

### Q: Detail the physical mechanisms of Zener vs. Avalanche breakdown in a reverse-biased PN junction.

- **Zener Breakdown**: occurs in **heavily doped** junctions, giving a very narrow depletion region. A relatively low reverse bias (< 5 V) creates a field strong enough to rip electrons directly out of covalent bonds via tunneling from the valence band to the conduction band. Has a **negative** temperature coefficient.
- **Avalanche Breakdown**: occurs in **lightly doped** junctions, giving a wider depletion region. Under higher reverse bias (> 5 V), minority carriers accelerate to high kinetic energies and collide with the lattice, breaking bonds and generating new electron-hole pairs (impact ionization) in a cascading effect. Has a **positive** temperature coefficient.

### Q: A PN junction diode exhibits two distinct capacitances depending on bias. Identify both, explain their physical mechanisms, and state which bias condition each dominates under.

- **Depletion (Junction) Capacitance, $C_j$** — dominant in **reverse bias**. The depletion region acts like the dielectric of a parallel-plate capacitor, sandwiched between the conductive p- and n-type neutral regions. Changing the reverse voltage changes the depletion width, uncovering more or fewer immobile dopant ions. Non-linear: $C_j$ decreases as reverse bias increases.
- **Diffusion Capacitance, $C_d$** — dominant in **forward bias**. Injected excess minority carriers establish a steady-state stored-charge profile in the neutral regions; changing the forward voltage requires this profile to shift to a new equilibrium. $C_d$ is typically orders of magnitude larger than $C_j$.

### Q: Explain the operating principles of clamping and limiting (clipping) circuits.

- **Limiter (Clipper)**: caps the input signal at a set threshold. Built from resistors and diodes; once the input exceeds the DC bias plus diode forward drop, the diode turns ON and clamps the output.
- **Clamper (DC Restorer)**: shifts the entire AC waveform up or down by a fixed DC level without altering its shape. Built from a capacitor, diode, and resistor — the capacitor charges rapidly to the input peak and holds it (given a large $RC$), acting like a DC battery in series with the input.

---

## 5. Short Answer Q&A

**Q: What is the Fermi Level?**
A: The energy level at which the probability of finding an electron is exactly 50% at thermal equilibrium.

**Q: Define carrier mobility ($\mu$).**
A: A measure of how easily a carrier moves through a semiconductor under an electric field ($v_d = \mu E$).

**Q: What is the depletion region?**
A: The region near a PN junction depleted of mobile charge carriers due to diffusion and recombination, leaving behind immobile charged impurity ions.

**Q: What is thermal voltage ($V_T$)?**
A: The voltage equivalent of a particle's thermal energy, $V_T = kT/q$. At 300 K it is approximately 25.9 mV.

**Q: What is the barrier (built-in) potential, $V_0$?**
A: The potential difference across the depletion region at thermal equilibrium, preventing further diffusion of majority carriers across the junction.

**Q: Why does a capacitor filter reduce ripple in a rectifier circuit?**
A: The capacitor charges to the peak of the rectified voltage and discharges slowly through the load as the wave drops below the peak. With a large $RC$ time constant, the output stays close to the peak, smoothing the wave.

---

*End of EDC Master Reference README — Units 1 & 2, Complete*
