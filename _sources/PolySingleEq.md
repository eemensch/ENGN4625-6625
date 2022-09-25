# Polyphase Systems

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
V{c1} - V_{c2} &= \jmath \omega LI_c + \jmath \omega M (I_a + I_b)
\end{align*}
$$

If the currents form a balanced set:

$$
Ia + Ib + Ic = 0
$$ (balanced_I)

Then the voltage drops are simply

$$
\begin{align*}
V_{a1} - V_{a2} &= \jmath \omega \overbrace{( L -M)}^{:= L_1} I_a \\
V_{b1} - V_{b2} &= \jmath \omega ( L -M)I_b\\
V{c1} - V_{c2} &= \jmath \omega ( L -M)I_c
\end{align*}
In this case, an apparent inductance, suitable for the balanced case, $L_1$, describes the behaviour of one phase in terms of its own current. It is most important
to note that this inductance is a valid description of the line only if {eq}`balanced_I` holds.
