# Polyphase Systems

Most electric power applications employ three phases, that is, three-separate power-carrying circuits, with voltages and currents staggered symmetrically in time are used.
Two major reasons for the use of three-phase power are
- economical use of conductors and
- nearly constant power flow.

Systems with more than one phase are generally termed polyphase. Three-phase systems are the most common, but there are situations in which a different number of phases may be used. Two-phase systems have a simplicity that makes them useful for teaching vehicles and for certain servomechanisms. This is why two-phase machines show up in laboratories and textbooks. Systems with a relatively large number of phases are used for certain specialised applications such as controlled rectifiers for aluminium smelters. Six-phase systems have been proposed for very high power transmission applications. Five-phase systems are sometimes used for motor drives with high reliability requirements.

Polyphase systems are qualitatively different from single-phase systems. In some sense polyphase systems are more complex, but often much easier to analyse. This little paradox
will become obvious during the discussion of electric machines. It is interesting to note that
physical conversion between polyphase systems of different phase number is always
possible.

## Two-phase System

The two-phase system is the simplest of all polyphase systems to describe. Consider a pair of voltage sources with

$$
  \mathbf{V}_1=V\cos\omega t = \Re\left \{V \mathrm{e}^{\jmath \omega t} \right \}, \qquad \mathbf{V}_2=V\cos(\omega t - \frac{\pi}{2}) = \Re\left \{V \mathrm{e}^{\jmath (\omega t-\frac{\pi}{2})}\right \}
$$
Suppose this system of sources is connected to a "balanced load", as shown in {numref}`2phase`.
```{figure} fig/poly/main-figure16.svg
---
width: 700px
name: 2phase
---
A two-phase systems and the phasor diagram of the two phase voltage source (right)
```
Here, "balanced" means both load impedances have the same value $Z$. To compute the power flows in the system, it is convenient to re-write the voltages in complex form. If each source is connected to a load with impedance,

$$
\mathbf{Z} = Z \mathrm{e}^{\jmath \psi}.
$$
then each of the two-phase networks has the same value
for real and reactive power:

$$
\begin{align*}
  S_1= P_1+\jmath Q_1 &= \dfrac{1}{2} \mathbf{V}_1 I_1^* = \dfrac{1}{2} \mathbf{V}_1  \dfrac{\mathbf{V}_1^*}{\mathbf{Z}^*} = \dfrac{V^2}{2Z}\cos\psi +\jmath \dfrac{V^2}{2Z}\sin\psi \\&= \dfrac{1}{2} \mathbf{V}_2 \mathbf{I}_2^* = \dfrac{1}{2} \mathbf{V}_2  \dfrac{\mathbf{V}_2^*}{\mathbf{Z}^*} =P_2+\jmath Q_2 = S_2
\end{align*}
$$

Using {eq}`eq_piv` the instantaneous power is

$$
\begin{align*}
  p_1 &=  \dfrac{V^2}{2Z} \cos\psi (1+\cos 2\omega t) + \dfrac{V^2}{2Z}\sin\psi \sin 2\omega t \\
  p_2 &= \dfrac{V^2}{2Z} \cos\psi (1+\cos (2\omega t - \pi)) + \dfrac{V^2}{2Z}\sin\psi \sin (2\omega t - \pi)
\end{align*}
$$
Note that the time-varying parts of these two expressions have opposite signs. Added together, they give instantaneous power:

$$
p_1+p_2 = \dfrac{V^2}{Z} \cos\psi
$$
At least one of the advantages of polyphase power networks is now apparent. The use of a balanced polyphase system avoids the power flow pulsations due to ac voltage and current, and even the pulsations due to reactive energy flow. This has obvious benefits when dealing with motors and generators or, in fact, any type of source or load for which constant power is advantageous.

## Three-Phase Systems

Consider the arrangement of three voltage sources illustrated in {numref}`3phase`.

```{figure} fig/poly/main-figure19.svg
---
width: 200px
name: 3phase
---
Voltage source arrangement in a three-phase system
```
Assume that the three-phase voltages are

$$
\begin{align}
v_a &=V\cos\omega t = \Re\left \{V \mathrm{e}^{\jmath \omega t} \right \}, \\
v_b &=V\cos(\omega t - \frac{2\pi}{3}) = \Re\left \{V \mathrm{e}^{\jmath (\omega t-\frac{2\pi}{3})}\right \}\\
v_c &=V\cos(\omega t + \frac{2\pi}{3}) = \Re\left \{V \mathrm{e}^{\jmath (\omega t + \frac{2\pi}{3})}\right \}
\end{align}
$$ (eq_vn)
The waveforms in time domain are presented in {numref}`3phase_voltage`.
```{figure} fig/poly/main-figure18.svg
---
width: 500px
name: 3phase_voltage
---
The voltage waveforms in a three-phase system
```
```{figure} fig/poly/main-figure20.svg
---
name: spin_phasor
width: 200px
align: center
figclass: margin
---
Phasor diagram: three-phase voltages.
```
The instantaneous voltages may be visualised by imagining {numref}`spin_phasor` where the vectors spin counterclockwise with angular velocity $\omega$. The instantaneous voltages are just projections of the vectors of this “pinwheel” onto the horizontal axis.

Consider connecting these three voltage sources to three identical loads, each with complex impedance $\mathbf{Z}$, as shown in {numref}`3p_balanced`

```{figure} fig/poly/main-figure21.svg
---
name: 3p_balanced
width: 500px
align: center
---
Three-phase voltage sources connected to a balanced load.
```
If voltages are as given above, then the currents in the three phases are

$$
\begin{align*}
i_a &= \Re\left \{\dfrac{\mathbf{V}}{\mathbf{Z}} \mathrm{e}^{\jmath \omega t} \right \}\\
i_b &= \Re\left \{\dfrac{\mathbf{V}}{\mathbf{Z}} \mathrm{e}^{\jmath (\omega t-\frac{2\pi}{3})} \right \}
\\
i_c &= \Re\left \{\dfrac{\mathbf{V}}{\mathbf{Z}} \mathrm{e}^{\jmath (\omega t+\frac{2\pi}{3})} \right \}
\end{align*}
$$
and the complex power is

$$
S = P+\jmath Q= \dfrac{V^2}{2 Z} (\cos \psi +\jmath \sin \psi)
$$

Remembering the time phase of the three sources, it is possible to write the values of instantaneous power in the three phases:

$$
\begin{align*}
  p_a & = \dfrac{V^2}{2 |Z|} \left [ \cos{\psi} (1+\cos 2\omega t) + \sin \psi \sin 2\omega t \right ]\\
  p_b & = \dfrac{V^2}{2 |Z|} \left [ \cos{\psi} (1+\cos 2(\omega t - 2\pi/3) + \sin \psi \sin 2(\omega t - 2\pi/3) \right ]\\
  p_c & = \dfrac{V^2}{2 |Z|} \left [ \cos{\psi} (1+\cos 2(\omega t + 2\pi/3)) + \sin \psi \sin 2(\omega t + 2\pi/3) \right ]
\end{align*}
$$
The sum of these three expressions is total instantaneous power, which is constant:

$$
  p=p_a+p_b+p_c = \dfrac{3}{2} \dfrac{V^2}{Z}\cos\psi.
$$

Moreover, the current in the neutral wire, $i_n$, in {numref}`3p_balanced`, is

$$
i_n=i_a+i_b+i_c =0
$$
This shows the most important advantage of three-phase systems over two-phase systems:
_a wire with no current in it does not have to be very large_. In fact, the neutral connection may be eliminated completely in many cases.

There is a fundamental difference between grounded and ungrounded systems if perfectly balanced conditions are not maintained. In effect, the ground wire provides isolation between the phases by fixing the neutral voltage at the star point to be zero. If the load impedances are not equal the load is said to be _unbalanced_. If an unbalanced system is grounded
there may be current in the neutral. If an unbalanced load is not grounded, the star point (see {numref}`3p_balanced`) voltage may not be zero, and the voltages will be different in the three phases at the load, even if the voltage sources all have the same magnitude.
```{figure} fig/poly/main-figure22.svg
---
name: ll
width: 200px
align: center
figclass: margin
---
From line&ndash;neutral to line&ndash;line Voltage Phasors
```

```{figure} fig/poly/main-figure23.svg
---
name: llln
width: 200px
align: center
figclass: margin
---
line&ndash;neutral and line&ndash;line Voltage Phasors
```
## Line&ndash;Line Voltages
A balanced three-phase set of voltages has a well-defined set of line&ndash;line voltages. If the line&ndash;neutral voltages are given by {eq}`eq_vn`, then line&ndash;line voltages are

$$
\begin{align}
\mathbf{V}_{ab} &= v_a - v_b = \Re \left \{ V \left (1-\mathrm{e}^{-\jmath \frac{2\pi}{3}}\right ) \mathrm{e}^{\jmath \omega t} \right \} = \Re \left \{ \sqrt{3} V \mathrm{e}^{\jmath \frac{\pi}{6}} \mathrm{e}^{\jmath \omega t}\right \}\\
\mathbf{V}_{bc} &= v_b - v_c = \Re \left \{ V \left (\mathrm{e}^{-\jmath \frac{2\pi}{3}}- \mathrm{e}^{\jmath \frac{2\pi}{3}}\right ) \mathrm{e}^{\jmath \omega t} \right \}= \Re \left \{ \sqrt{3} V \mathrm{e}^{\jmath \frac{-\pi}{2}}\mathrm{e}^{\jmath \omega t} \right \}\\
\mathbf{V}_{ca} &= v_c - v_a = \Re \left \{ V \left (\mathrm{e}^{\jmath \frac{2\pi}{3}} - 1 \right ) \mathrm{e}^{\jmath \omega t} \right \}= \Re \left \{ \sqrt{3} V \mathrm{e}^{\jmath \frac{5\pi}{6}} \mathrm{e}^{\jmath \omega t} \right \}
\end{align}
$$
The phasor relationship of line&ndash;neutral and line&ndash;line voltages is shown in {numref}`ll` and {numref}`llln`.


Two
things should be noted about this relationship:
- The line&ndash;line voltage set has a magnitude that is larger than the line&ndash;neutral voltage by a factor of 3.
- Line&ndash;line voltages are phase shifted by 30 with respect to the line&ndash;neutral voltages.

Line&ndash;line  voltages themselves form a three-phase set just as line&ndash;neutral voltages do. This is shown conceptually in {numref}`YD_source`.
```{figure} fig/poly/main-figure24.svg
---
name: YD_source
width: 600px
align: center
---
Wye (Y) and delta ($\Delta$) connected voltage sources
```
Power system components (sources, transformer windings, loads, etc.) may be connected either line&ndash;neutral or line&ndash;line. The former
connection is often called wye, the latter is called delta, for obvious reasons. It should be noted that the wye connection is at least potentially a four-terminal connection, and could be grounded or ungrounded. The delta connection is inherently three-terminal and necessarily ungrounded.

```{prf:example} Wye-and Delta-connected Loads


Loads may be connected in either line&ndash;neutral or line&ndash;line configuration. An example of the
use of this flexibility is in a fairly commonly used distribution system with a line&ndash;neutral
voltage of 120 V, RMS (about 170 V, peak). In this system the line&ndash;line voltage is 208 V, RMS
(about 294 V, peak). Single-phase loads may be connected either line&ndash;line or line&ndash;neutral.
Suppose it is necessary to build a resistive heater to deliver 6 kW, to be made of three elements which may be connected in either wye or delta. Each of the three elements must dissipate 2000 W.

Thus, since $P =\dfrac{V^2}{R}$, the wye-connected resistors would be

$$
R_Y =  \dfrac{120^2}{2000} =  7.2
$$
while the delta-connected resistors would be

$$
R_\Delta =  \dfrac{208^2}{2000} =  21.6
$$
```
As is suggested by this example, wye- and delta-connected impedances are often directly
equivalent. In fact, ungrounded connections are three-terminal networks which may be
represented in two ways. The two networks shown in {numref}`YD`, combinations of three passive impedances, are directly equivalent and identical in their terminal behaviour if the relationships between elements are as given below

$$
\begin{align*}
  Z_{ab} &=  \dfrac{Z_a Z_b + Z_b Z_c + Z_c Z_a}{Z_c},\\ Z_{bc} &=  \dfrac{Z_a Z_b + Z_b Z_c + Z_c Z_a}{Z_a},\\ Z_{ca} &=  \dfrac{Z_a Z_b + Z_b Z_c + Z_c Z_a}{Z_b}
\end{align*}
$$ (D_in_Y)

$$
\begin{align*}
Z_{a} &=  \dfrac{Z_{ab} Z_{ca}}{Z_{ab}+Z_{bc}+Z_{ca}},\\ Z_{b} &=  \dfrac{Z_{ab}Z_{bc}}{Z_{ab}+Z_{bc}+Z_{ca}},\\ Z_{c} &=  \dfrac{Z_{bc}+Z_{ca}}{Z_{ab}+Z_{bc}+Z_{ca}}
\end{align*}
$$ (Y_in_D)
```{figure} fig/poly/main-figure25.svg
---
name: YD
width: 600px
align: center
---
Wye (Y) and delta ($\Delta$) connected loads
```

For the special case of balanced loads where

$$
Z_a=Z_b=Z_c = Z_Y
$$
and

$$
Z_{ab} = Z_{bc} = Z_{ca} =  Z_{\Delta}
$$
Then,

$$
Z_\Delta = 3 Z_Y
$$

````{prf:example} Use of Wye–Delta for Unbalanced Loads

Consider the unbalanced load connected to a balanced voltage source as presented below.

```{image} fig/poly/main-figure28.svg
:width: 500px
:align: center
```
The problem is to determine the line currents. Note that this load is ungrounded (if it were grounded, this would be a trivial problem). The voltages are given by

$$
\begin{align}
v_a &= V\cos\omega t\\
v_b &= V\cos \left ( \omega t -\dfrac{2\pi}{3}\right )\\
v_c &= V\cos \left ( \omega t +\dfrac{2\pi}{3}\right )
\end{align}
$$
To solve this problem, we convert the source to delta equivalent and use {eq}`D_in_Y` convert the load to delta equivalent as shown in the circuit below.
```{image} fig/poly/main-figure29.svg
:width: 500px
:align: center
```
Thus, the values of the three resistors in $\Delta$ configuration are

$$
\begin{align}
R_{ab}&=R_{ca}=\dfrac{2+4+2}{2}=4\\
 R_{bc}&=\dfrac{2+4+2}{1}=8
 \end{align}
 $$
 The complex amplitudes of the equivalent voltage sources are

 $$
 \begin{align*}
   \mathbf{V}_{ab}&=\mathbf{V}_a-\mathbf{V}_b = \sqrt{3}V \mathrm{e}^{\jmath\frac{\pi}{6}}\\
   \mathbf{V}_{bc}&=\mathbf{V}_b-\mathbf{V}_c = \sqrt{3}V \mathrm{e}^{-\jmath\frac{\pi}{2}}\\
   \mathbf{V}_{ca}&=\mathbf{V}_c-\mathbf{V}_a = \sqrt{3}V \mathrm{e}^{\jmath\frac{5\pi}{6}}\\
  \end{align*}
  $$

  The currents in each of the equivalent resistors are

  $$
  \begin{align*}
    \mathbf{I}_{ab}=\dfrac{\mathbf{V}_{ab}}{R_{ab}}, \; \mathbf{I}_{bc}=\dfrac{\mathbf{V}_{bc}}{R_{bc}}, \; \mathbf{I}_{ca}=\dfrac{\mathbf{V}_{ca}}{R_{ca}}
   \end{align*}
  $$
  The line currents are then just the difference between current in the legs of the delta:

  $$
  \begin{align*}
  \mathbf{I}_a &= \mathbf{I}_{ab}-\mathbf{I}_{ca} = \dfrac{3}{4}V\\
  \mathbf{I}_b &= \mathbf{I}_{bc}-\mathbf{I}_{ab} = -\left (\dfrac{3}{8} +\jmath\dfrac{\sqrt{3}}{4} \right ) V\\
  \mathbf{I}_c &= \mathbf{I}_{ca}-\mathbf{I}_{bc} = -\left (\dfrac{3}{8} -\jmath\dfrac{\sqrt{3}}{4} \right ) V.
  \end{align*}
  $$
  ````

## Summary

We were introduced to the notion of polyphase systems and observed some of the benefits of such systems. We further studied the relationship between wye and delta connections in three-phase systems.
