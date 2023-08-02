# Polyphase Lines and Single-phase Equivalents

Although the three phases in a balanced polyphase system are physically interconnected they may be considered as three single-phase systems. This is reinforced by the equivalence between wye- and delta-connected sources and impedances. One more step is required to show that single-phase equivalence has merit, and this concerns situations in which the phases have mutual coupling.

## Polyphase Transmission and Distribution Lines

_Lines_ are system elements as transmission or distribution lines: overhead wires, cables or in-plant buswork. Such elements have impedance, so that there is some voltage drop
between the two ends of the lines (called _sending_ and _receiving_ ends). This impedance is more than just conductor resistance: the conductors have both self and mutual inductance because currents in the conductors make magnetic flux which, in turn, is linked by all conductors of the line.

The phase conductors are arranged as parallel conductors in bundles. These wires are supported by insulators. In many cases these insulators are actually strings of individual plates, often made of ceramic material, arranged to have a very
long surface between the conductor and ground. Usually there are also accompanying ground wires that serve to carry the inevitable but usually small neutral currents that result
from system unbalance and fault currents, and that partially shield the active conductors from lightning.

A schematic view of a line is shown {numref}`mutual_coupling`. Actually, only the inductance components of line impedance are shown, since they are the most interesting parts of line impedance. A simplifying approximation is made that the mutual inductance is the same for all pairs of conductors.

```{figure} fig/poly/mutual_coupling.png
---
width: 700px
name: mutual_coupling
---
Schematic of a balanced three-phase line with mutual coupling.
```
Working in complex amplitudes, it is possible to write the voltage drops for the three phases by

$$
\begin{align*}
V_{a1} - V_{a2} &= \jmath \omega L I_a + \jmath \omega M (I_b + I_c)\\
V_{b1} - V_{b2} &= \jmath \omega LI_b + \jmath \omega M (I_a + I_c)\\
V_{c1} - V_{c2} &= \jmath \omega LI_c + \jmath \omega M (I_a + I_b)
\end{align*}
$$

If the currents form a balanced set:

$$
I_a + I_b + I_c = 0
$$ (balanced_I)

Then the voltage drops are

$$
\begin{align*}
V_{a1} - V_{a2} &= \jmath \omega \overbrace{( L -M)}^{:= L_\ell} I_a \\
V_{b1} - V_{b2} &= \jmath \omega ( L -M)I_b\\
V_{c1} - V_{c2} &= \jmath \omega ( L -M)I_c
\end{align*}
$$

In this case, an apparent inductance, suitable for the balanced case, $L_\ell$, describes the behaviour of one phase in terms of its own current. It is most important
to note that this inductance is a valid description of the line only if {eq}`balanced_I` holds.

````{prf:example}

A three-phase resistive load is connected to a balanced three-phase source through a transformer connected in delta&ndash;wye and a polyphase line, as depicted below. Calculate power dissipated in the load resistors.

```{image} fig/poly/M_example.png
:width: 700px
:align: center
```
The three-phase voltage source satisfies:

$$
\begin{align*}
v_a &= \Re\left \{\sqrt{2}V_{RMS} \mathrm{e}^{\jmath \omega t} \right \}, \\
v_b &= \Re\left \{\sqrt{2}V_{RMS} \mathrm{e}^{\jmath (\omega t-\frac{2\pi}{3})}\right \}\\
v_c &= \Re\left \{\sqrt{2}V_{RMS} \mathrm{e}^{\jmath (\omega t + \frac{2\pi}{3})}\right \}
\end{align*}
$$
We apply a succession of simple transformations. First, the delta-connected resistive load is converted to its equivalent wye with $R_Y = R/3$.

Next, since the problem is balanced, the self- and mutual inductances of the line are
directly equivalent to self-inductances in each phase of $L_\ell = L - M$.
Now, the transformer secondary is facing an impedance in each phase of

$$
\mathbf{Z} =  R_Y + \jmath \omega L_\ell.
$$

The delta-wye transformer has a voltage ratio of

$$
\dfrac{v_p}{v_s} = \dfrac{N_\Delta}{\sqrt{3}N_Y}.
$$

On the primary side of the transformer, the line and load impedance is

$$
\mathbf{Z}_p =  R_{eq} + \jmath \omega L_{eq},
$$
where

$$
\begin{align*}
L_{eq} &= \dfrac{1}{3} \left ( \dfrac{N_\Delta}{N_Y} \right)^2 (L-M)\\
R_{eq} &= \dfrac{1}{3} \left ( \dfrac{N_\Delta}{N_Y} \right)^2 \dfrac{R}{3}.
\end{align*}
$$

The magnitude of current flowing in each phase of the source is

$$
|\mathbf{I}| = \dfrac{\sqrt{2} V_{RMS}}{\sqrt{(\omega L_{eq})^2 + R_{eq}^2}}
$$
Power dissipation in each phase is

$$
P= \dfrac{1}{2} |\mathbf{I}|^2 R_{eq} =  \dfrac{ V_{RMS}^2 R_{eq}}{(\omega L_{eq})^2 + R_{eq}^2}
$$
Total power dissipated is three times the single-phase dissipation.

````

## Per-unit System

Per-unit systems are nothing more than normalisations of voltage,
current, impedance, and power. These normalisations of system parameters are used
because they provide simplifications in many network calculations. As we will discover, while certain ordinary parameters have very wide ranges of value, the equivalent per-unit parameters fall in a much narrower range. This helps in understanding how certain types of system behave and looking past the "numbers".

### Normalisation of Voltage and Current

The basis for the per-unit system of notation is the expression of voltage and current as fractions of base levels. Thus the first step in setting up a per-unit normalisation is to pick base voltage and current.

Consider a network where an impedance $\mathbf{Z}$ is connected to a voltage source $\mathbf{V}$, the complex amplitudes of voltage and current satisfy

$$
\mathbf{V} = \mathbf{I} \mathbf{Z}.
$$

Start by defining two base quantities, $V_B$ for voltage and $I_B$ for current. In many cases,
these will be chosen to be nominal or rated values of the generators or transformers in the network (or the portion that is being studied). For generating plants, for example, it is common to use the rated voltage and rated current of the generator as base quantities.
In other situations, such as system stability studies, it is common to use a standard, system-wide base system.

The per-unit voltage and current are

$$
\mathbf{v} =  \dfrac{\mathbf{V}}{V_B},\qquad \mathbf{i} =  \dfrac{\mathbf{I}}{I_B}
$$

Consequently, the per-unit impedance is

$$
\mathbf{z} =  \dfrac{\mathbf{Z}}{\mathbf{Z}_B},
$$
where $\mathbf{Z}_B$ is a base impedance and is defined as

$$
\mathbf{Z}_B := \dfrac{V_B}{I_B}
$$

This will also lead to the definition of a base power, which for a single phase system is

$$
P_B = V_B I_B
$$
where $V_B$ and $I_B$ are RMS values.

As long as normalisation is carried out in a consistent way, there is no ambiguity in per-unit notation, that is,
peak quantities normalised to peak base quantities will be the same, in per-unit, as RMS quantities normalised to RMS bases.

### Three-phase Systems

When describing polyphase systems, we have the choice of using either line&ndash;line or line&ndash;neutral voltage and line current or current in delta equivalent loads. In order to keep straight analysis in ordinary variables, it is necessary to carry along information about which of these quantities is being used. There is no such problem with per-unit notation.
We may use as base quantities either line to neutral voltage $V_{B,l-n}$ or line to line voltage $V_{B,l-l}$. Taking the base current to be line current $I_{Bl}$, we may express base power as

$$
P_B = 3 V_{B,l-n} I_{Bl}.
$$

Because line&ndash;line voltage is, under normal operation, $\sqrt{3}$ times line–neutral voltage, equivalent statement is

$$
P_B = \sqrt{3} V_{B,l-l} I_{Bl}.
$$

If base impedance is expressed by line&ndash;neutral voltage and line current (this is the common convention, but is not required),

$$
Z_B =  \dfrac{V_{B,l-n}}{I_{Bl}}
$$

Then, base impedance is, written in terms of base power,

$$
Z_B =  \dfrac{P_B}{3I^2_B} = 3 \dfrac{V_{B,l-n}^2}{P_B} = \dfrac{V_{B,l-l}^2}{P_B}  
$$

Note that a single per-unit voltage applies equally well to line&ndash;line, line&ndash;neutral, peak, and RMS quantities. For a given situation, each of these quantities will have a different ordinary value, but there is only one per-unit value.

### Networks with Transformers


One of the most important advantages of the use of per-unit systems arises in the analysis of networks with transformers. Properly applied, a per-unit normalisation will cause nearly all ideal transformers to disappear from the per-unit network, thus greatly simplifying the analysis.

Consider an ideal transformer with two windings and turn ratio of $N$ where

$$
\mathbf{V}_2 = N \mathbf{V}_1,\qquad \mathbf{I}_1 = N \mathbf{I}_2.
$$

Normalised to base quantities on the two sides of the transformer, the per-unit voltage and current are

$$
\begin{align*}
\mathbf{v}_1 &=  \dfrac{\mathbf{V}_1}{V_{B1}}\\
\mathbf{v}_2 &=  \dfrac{\mathbf{V}_2}{V_{B2}}\\
\mathbf{i}_1 &=  \dfrac{\mathbf{I}_1}{I_{B1}}\\
\mathbf{i}_2 &=  \dfrac{\mathbf{I}_2}{I_{B2}}
\end{align*}
$$

Now, note that if the base quantities are chosen as

$$
V_{B2} = N V_{B1},\qquad I_{B1} = N I _{B2}
$$
then $\mathbf{v}_1=\mathbf{v}_2$ and $\mathbf{i}_1 =\mathbf{i}_2$. In other words if the base quantities are selected in a way so that they related to each other as if they had been processed by the transformer, then the per-unit values of primary and secondary voltages and currents will be the same.

This observation highlights a general rule in setting up per-unit normalisations for systems with transformers. Each segment of the system should have the same base power. Base voltages transform according to transformer voltage ratios. For three-phase systems, of course, the voltage ratios differ from the physical turns ratios by a factor of $\sqrt{3}$ if delta-wye
or wye-delta connections are used. It is, however, the voltage ratio that must be used in setting base voltages.

### Transforming from One Base to Another

Often data such as transformer leakage inductance is given in per-unit terms, on some base (perhaps the unit's rating), while in order to do a system study it is necessary to express the same data in per-unit in some other base (perhaps a unified system base). It is always possible to do this by the two-step process of converting the per-unit data to its ordinary form, then re-normalising it in the new base. However, it is easier to just convert it to the
new base in the following way.
Note that impedance in Ohms (ordinary units) is given by

$$
\mathbf{Z} =  \mathbf{z}_1 Z_{B1}=\mathbf{z}_2 Z_{B2}.
$$

Here, of course, $\mathbf{z}_1$ and $\mathbf{z}_2$ are the same per-unit impedance expressed in different bases.
This could be written as

$$
\mathbf{z}_1\dfrac{V_{B1}^2}{P_{B1}}=\mathbf{z}_2 \dfrac{V_{B2}^2}{P_{B2}}
$$

This yields a convenient rule for converting from one base system to another:

$$
\mathbf{z}_1=\dfrac{P_{B1}}{P_{B2}}\left (  \dfrac{V_{B2}}{V_{B1}} \right )^2 \mathbf{z}_2
$$


````{prf:example} Fault Study

A one-line diagram is a way of conveying a lot of information about a power system without becoming cluttered with repetitive pieces of data. Drawing all three phases of a system would involve quite a lot of repetition that is not needed for most studies. Further, the three phases can be reconstructed from the one-line diagram if necessary. It is usual to use special symbols for different components of the network.

```{image} fig/poly/3phase_fault.png
:width: 700px
:align: center
```
The following table provides the necessary information for making sense of the diagaram:

Symbol |  Component | Base $P_B$, (MVA) | Base $V_B$ (kV) (line-to-line) | Impedance (per-unit)
|:--------------:|:-----:|:-----------:|:-----:|:-----------:|
$G_1$ |  Generator |200  | 13.8 | $\jmath 0.18$
$T_1$ |  Transformer | 200 | 13.8/138 | $\jmath 0.12$
$L$ |  Transmission Line | 100 | 138 | $0.02+\jmath 0.05$
$T_2$ |  Transformer | 50 | 138/34.5 | $\jmath 0.08$

A three-phase fault is assumed to occur on the 34.5 kV side of the transformer $T_2$. This is a symmetrical situation, so that only one phase must be represented. The per-unit impedance diagram is shown below. It is necessary to proceed now to determine the value of the components in this circuit.

```{image} fig/poly/imp_diag_fault.png
:width: 600px
:align: center
```
First, it is necessary to establish a uniform base per-unit value for each of the system components. In this case, all of the parameters are put into a base power of 100 MVA and voltage bases of 138 kV on the line, 13.8 kV at the generator, and 34.5 kV at the fault.

$$
\begin{align*}
\mathbf{x}_g &= \dfrac{100}{200} \times 0.18 = 0.09 \text{ per-unit}\\
\mathbf{x}_{T_1} &= \dfrac{100}{200} \times 0.12 = 0.06 \text{ per-unit}\\
\mathbf{x}_{T_2} &= \dfrac{100}{50} \times 0.08 = 0.16 \text{ per-unit}\\
\mathbf{r}_L &= 0.02 \text{ per-unit}\\
\mathbf{x}_L &= 0.05 \text{ per-unit}\\
\end{align*}
$$

The total impedance is

$$
\mathbf{z} =  \jmath (\mathbf{x}_g + \mathbf{x}_{T_1} +\mathbf{x}_L + \mathbf{x}_{T_2}) + +\mathbf{r}_L = \jmath 0.36 + 0.02 \text{ per unit}
$$

$$
|\mathbf{z}| =  0.361 \text{ per unit}
$$
Now, if $e_g$ is equal to one per-unit (generator internal voltage equal to base voltage), then the per-unit current is

$$
|\mathbf{i}| = \dfrac{1}{0.361} = 2.77 \text{ per unit}.
$$

This may be translated back into ordinary units by getting base current levels, which are

- on the base at the generator: $I_{B,G} = \dfrac{100 \text{MVA}}{\sqrt{3} \times 13.8 \text{kV}} = 4.18 \text{kA}$.
- on the line base: $I_{B,L} = \dfrac{100 \text{MVA}}{\sqrt{3} \times 138 \text{kV}} = 418$.
- on the base at the fault: $I_{B,F} = \dfrac{100 \text{MVA}}{\sqrt{3} \times 34.5 \text{kV}} = 1.67 \text{kA}$.

Then the actual fault currents are:

- at the generator: $|\mathbf{I}_f| = 11578.6 \text{A}$
- on the transmission line: $|\mathbf{I}_f|=1157.86 \text{A}$
- at the fault: $|\mathbf{I}_f| = 4625.9 \text{A}$
````
