# AC Voltage, Current, and Power

The basic quantities in electric power systems are voltage and current. Voltage is also called, suggestively, _electromotive force_. It is the pressure that forces electrons to move. Current is, of course, that flow of electrons. As with other descriptions of other types of power, electric power is that force (voltage) pushing on the flow (current). In order to understand electric power, one must first solve the circuit problems associated with flow of current in
response to voltage.

Most electric power systems, including all electric utility systems, employ alternating current. Voltages and currents very closely approximate sine waves. Thus, to understand the
circuit issues it is necessary to prepare to analyse systems with sinusoidal voltages and currents. Robust and relatively easy-to-use methods for handling sinusoidal quantities have been developed, and this is the subject material for this chapter.

In this chapter, we discuss voltage, current, and power in electric power systems. Particularly, we will
- refamiliarise ourselves with the basics of AC circuits and the important passive and active elements prevalent in power systems analysis;
- review the notion of active and reactive power;
- revisit the notion of sinusoidal steady state and complex circuit variables;

## Sources and Power

### Voltage and Current Sources
Consider the interconnection of two sources, as shown in {numref}`sources`. On the left is the symbol for a voltage source. This is a circuit element that maintains a voltage at its terminals, no matter what the current. On the right is the symbol for a current source. This
is the complementary element: it maintains current no matter what the voltage. Obviously, these are idealisations, but they do serve as good proxies for reality. For example, the
power system connection to a customer’s site is a good approximation to a voltage source.
On the other hand, some types of generator interconnections to the power system, such as those from solar photovoltaic power plants and some types of wind turbines, approximate current sources.

```{figure} fig/AC/main-figure0.svg
---
width: 300px
name: sources
---
Current source and voltage source interconnection, e.g., a solar plant connected to the power system.
```

If the voltage and current are both sine waves at the
same frequency, perhaps with a phase shift, they could be represented as

$$
\begin{align*}
v&= V \cos \omega t \\i &= I \cos (\omega t - \psi).
\end{align*}
$$
Remember that $\omega$ represent the frequency of the signal.

### Power

Note that Kirchhoff’s voltage and current laws (KVL and KCL), when applied here, specify that the voltage across the current source and the current through the voltage source are each specified by the other source. So power
out of the current source is also power in to the voltage source. If the angle $\psi$ is small so that the voltage and current are close to being in phase, the direction of positive power flow will be from the current source to the voltage source. That power flow will be

$$
\begin{align*}
  p = v i = V I \cos \omega t \cos (\omega t - \psi) = \dfrac{V I}{2} \left [ \underbrace{\cos \psi}_{power factor} + \cos (2\omega t - \psi) \right ]
\end{align*}
$$
The second equation follows from the trigonemetric relationship:

$$
\cos x \cos y = \dfrac{1}{2} \cos(x-y) + \dfrac{1}{2}\cos(x+y).$$

```{note}
Power has _an average value_ equal to $\dfrac{VI}{2}\cos\psi$ and $\cos\psi$ is known as the _power factor_. The power varies at twice the frequency of the other signals.
```

### Sinusoidal Steady State

We handle sine waves using complex notation. The key to understanding systems in the sinusoidal steady state is Euler’s relation:

$$
\mathrm{e}^{\jmath x} = \cos x +\jmath \sin x
$$
where $\jmath^2 =-1$ and $\mathrm{e}$ is the natural logarithm base equal to 2.718281828459\dots.

Consequently,

$$
\mathrm{e}^{\jmath \omega t } =  \cos \omega t +\jmath \sin \omega t$$
with

$$
\Re \{ \mathrm{e}^{\jmath \omega t} \} = \cos \omega t, \quad \Im \{ \mathrm{e}^{\jmath \omega t} \} = \sin \omega t
$$
A pure sinusoidal voltage $v(t)$ with no DC values can be always written as

$$
v(t) =  V \cos (\omega t + \phi) = \Re\{V \mathrm{e}^{\jmath \phi } \mathrm{e}^{\jmath \omega t } \}.
$$
This is the real part of a complex exponential with
continuously increasing phase angle. In this case the complex amplitude of the voltage is as shown in {numref}`phasor`:

$$
\mathbf{V} = V \mathrm{e}^{\jmath \phi}.
$$


```{figure} fig/AC/main-figure1.svg
---
width: 200px
name: phasor
---
Voltage phasor.
```

### Phasor Notation

The magnitude of this phasor, $V$, is the length of the vector, while the phase angle $\phi$ is represented by a rotation of the vector about its origin. The instantaneous value of the voltage is equal to the projection onto the horizontal axis of the tip of a vector that is rotating with angular velocity $\omega$ that is at the position of the voltage phasor at time $t = 0$.

### Real and Reactive Power

In a circuit such as that of {numref}`sources` in which there exists both voltage and current, as represented by two phasors in {numref}`phasors`, the voltage and current are

$$
v = \Re\{V \mathrm{e}^{\jmath (\omega t + \phi ) } \}, \quad i= \Re\{I \mathrm{e}^{\jmath (\omega t + \phi -\psi) } \}
$$

```{figure} fig/AC/main-figure2.svg
---
width: 200px
name: phasors
---
Voltage and current phasors.
```

Note that $\Re\{X\} = \dfrac{1}{2} ( X + X^*)$, then instantaneous power (as depicted in {numref}`piv`) is

$$
\begin{align}
  p &= \dfrac{1}{2}V I\cos\psi + \dfrac{1}{2}V I \cos (2(\omega t+ \phi) - \psi) \nonumber\\
  &= \dfrac{1}{2}V I \left(  \cos\psi  (1 + \cos 2 (\omega t +\phi)) + \sin\psi \sin 2(\omega t +\phi) \right ).
\end{align}
$$ (eq_piv)
there are two principal terms here. One is for the real
or time-average power:

$$
P =\dfrac{VI}{2}\cos\psi
$$

The other term has no time average, but represents power that is being exchanged between source and sink at twice the electrical frequency. This
is reactive power:

$$
Q =\dfrac{VI}{2}\sin\psi
$$

and it plays a very important role in controlling voltage in electric power systems.


```{figure} fig/AC/main-figure3.svg
---
width: 600px
name: piv
---
Instantaneous power, voltage, and current as a function of time with $\cos\psi = 0.8$ (i.e. power factor of 0.8).
```


Note that the apparent power is just the magnitude of real plus reactive power, assuming reactive is "imaginary" in the real/imaginary number plane:

$$
\begin{align*}
S &= P+\jmath Q = \dfrac{1}{2} \mathbf{V} \mathbf{I}^*\\
|S| &= |P+\jmath Q| = \dfrac{1}{2} |\mathbf{V}|\ |\mathbf{I}|
\end{align*}
$$

Here, real power is measured in _watts_ (W), apparent power is measured in _volt-amperes_ (VA) and reactive power is measured in _volt-amperes reactive_ (VARs). An example is depicted in {numref}`powers`.

```{figure} fig/AC/main-figure4.svg
---
width: 600px
name: powers
---
Apparent power, real power, and reactive power as a function of frequency $\omega = 2\pi f$ with $\cos\psi = 0.8$ (i.e. power factor of 0.8).
```


```{admonition} Root Mean Square (RMS) Amplitude
It is common to refer to voltages and currents by their RMS amplitudes, rather than peak. For sine waves the RMS amplitude is $1/\sqrt{2}$ of the peak amplitude. Thus, if the RMS amplitudes are $V_{RMS}$ and $I_{RMS}$, respectively,

$$
S = P+\jmath Q = \mathbf{V}_{RMS} \mathbf{I}_{RMS}^*
$$
```
## Resistors, Inductors, and Capacitors

These three linear, passive elements can be used to understand
much of what happens in electric power systems, and electrical engineering in general.

The resistor has the simple voltage–current relationship
```{figure} fig/AC/main-figure5.svg
---
width: 150px
align: center
figclass: margin
---
A resistor.
```

$$
i=\dfrac{v}{R}.
$$
As  voltage and current are in phase when driven by a voltage source

$$
I_{RMS} = \dfrac{V_{RMS}}{R}
$$
and complex power into the resistor is

$$
P+\jmath Q= V^2_{rms}/R.
$$

That is, the resistor draws only real power and reactive power
at its terminals is zero.

The inductor has the voltage–current relationship
```{figure} fig/AC/main-figure6.svg
---
width: 150px
align: center
figclass: margin
---
An iductor.
```

$$
v=L\dfrac{\mathrm{d} i}{\mathrm{d} t}
$$

In sinusoidal steady state:

$$
\mathbf{V} = \jmath \omega L \mathbf{I}
$$
and the complex power is

$$
P+\jmath Q = \mathbf{V}_{RMS} I^*_{RMS} = \jmath \dfrac{|\mathbf{V}_{RMS}|^2}{\omega L}.
$$
Thus, the inductor draws reactive power and ideally consumes no real power.
Of course real inductors have
some resistance, so the real power into an inductor will not be exactly zero, but in most cases
it will be small compared with the reactive power drawn. The inductor has _reactance_ $X_L = \omega L$.

The capacitor has a voltage–current relationship given by
```{figure} fig/AC/main-figure7.svg
---
width: 150px
align: center
figclass: margin
---
A capacitor.
```

$$
i=C\dfrac{\mathrm{d} v}{\mathrm{d} t}
$$
In sinusoidal steady state

$$
\mathbf{I} = \jmath \omega C \mathbf{V}.$$
This means that complex (real plus reactive) power drawn by
the capacitor is

$$
P+\jmath Q = \mathbf{V}_{RMS} \mathbf{I}^*_{RMS} = - \jmath |\mathbf{V}_{RMS}|^2 \omega C
$$

The capacitor is a source of reactive power. As with the inductor, the capacitor draws little real power. The idealised capacitor sources reactive power and draws zero real power. The
capacitor has reactance $X_C = - \dfrac{1}{\omega C}$.

### Reactive Power and Voltage

Reactive power plays a very important role in voltage
profiles on electric power systems. For that reason, it
is useful to start understanding the relationship
between reactive power and voltage from the very
start. Consider the simple circuit shown in the top figure in
{numref}`RL`.
```{figure} fig/AC/main-figure8.svg
---
name: RL
width: 300px
align: center
figclass: margin
---
An RL circuit driven by a sinusoidal voltage source (top). The voltage phasors in an RL circuit driven by a sinusoidal voltage source (middle).  The circuit after introducing a parallel capacitor (bottom).
```
A voltage source is connected to a resistive
load through an inductance. This is somewhat like a
power system, where transmission and distribution
lines are largely inductive. The voltage across the
resistor is

$$
\mathbf{V} = \mathbf{V}_g \dfrac{R}{R+\jmath \omega L }
$$
 The relationship between the complex vectors is depicted in the midle diagram of {numref}`RL`.

 The receiving end voltage is less than the
 source voltage, and the inequality will increase as
 the load increases (meaning current through the
 inductor increases). Consider what happens, however, when a capacitance is put in parallel with the resistor as shown in the bottom circuit of {numref}`RL`.

The voltages satisfy the following

$$
\begin{align*}
   \mathbf{V} &= \mathbf{V}_g \dfrac{\frac{R}{\jmath \omega C}}{\frac{R}{\jmath \omega C} + \jmath \omega L} \\&= \mathbf{V}_g \dfrac{1}{(1-\omega^2 LC) + \frac{\jmath \omega L}{R}}
\end{align*}
$$
````{prf:example}

Suppose the voltage source in the circuit of the bottom circuit of {numref}`RL` provides a sine wave with an RMS magnitude of $V_{g,RMS} = 10 kV$, the load resistor is $R = 10 \Omega$, the inductance is $L = 10$ mH, and the system frequency is $\omega = 2\pi × 60$ Hz = 377 rad/s. The relative magnitude of the output voltage is calculated as a function of the capacitor value and is shown  below.

```{image} fig/AC/main-figure10.svg
:width: 700px
:align: center
```
````
### Reactive Power Voltage Support

Capacitors providing reactive power suggests that positive reactive power
injection can provide some amount of voltage control. Indeed this is the case, and in distribution systems, electric power utilities often use capacitors usually switched in increments, to help control voltage profiles. To approach this problem, consider the arrangement shown below.

```{figure} fig/AC/main-figure11.svg
---
name: support
width: 300px
align: center
---
Power circuit with a generalised reactive element.
```

Here, the capacitor is replaced by a more general reactive admittance, defined by

$$
\mathbf{I} =\jmath B \mathbf{V}.
$$

The voltage across the load resistor is found using the same calculation as for the capacitor case and is

$$
\dfrac{\mathbf{V}}{\mathbf{V}_g} = \dfrac{R}{R(I - \omega L B ) + \jmath \omega L}
$$
Reactive power produced by the reactive element is

$$
Q =|\mathbf{V}|^2 B.
$$
These calculations may be carried out over a range of values of the reactive element $B$ and then voltage $|\mathbf{V}|$ plotted against reactive power $Q$ to get the effect of reactive power on voltage. The plot below shows how injection of reactive power affects voltage.
```{image} fig/AC/main-figure12.svg
:width: 700px
:align: center
```

## Voltage Stability

In some situations, loads (real and/or reactive) are controlled to be independent of voltage. These sorts of loads produce interesting behaviour.

The situation is illustrated in {numref}`RL1`.
```{figure} fig/AC/main-figure13.svg
---
name: RL1
width: 300px
align: center
---
Power circuit with a generalised reactive element.
```
A voltage source is driving some load that is adjusting its impedance to draw a certain amount of real and reactive power. The question is, what is the voltage across that load? This is a situation that is more common than you might
think: there are many "constant power" loads or loads that approximate constant power, for example many electronic power supplies and induction motors. We approach this by seeing that receiving end power is (dropping the RMS subscript unless it is needed.)

$$
P + jQ = \mathbf{V} \mathbf{I}^*
$$


Assuming that $V_g$ is real, the load voltage is

$$
\begin{align*}
  \mathbf{V} &= V_g - \overbrace{(R+j\omega L)}^{\mathbf{Z}} \mathbf{I} = V_g - \mathbf{Z}\dfrac{P - \jmath Q}{\mathbf{V}^*} \overset{\times \mathbf{V}^*}{\Longrightarrow}\\
  |\mathbf{V}|^2 &= V_g \mathbf{V}^* - \mathbf{Z}(P-\jmath Q){\Longrightarrow}
  \mathbf{V} = \dfrac{|\mathbf{V}|^2}{V_g} + \dfrac{\mathbf{Z}^*(P + \jmath Q))}{V_g}{\Longrightarrow}\\
  |\mathbf{V}|^2 &= \left ( \dfrac{|\mathbf{V}|^2}{V_g} + \dfrac{\mathbf{Z}^*(P + \jmath Q))}{V_g} \right )\left ( \dfrac{|\mathbf{V}|^2}{V_g} + \dfrac{\mathbf{Z}(P - \jmath Q))}{V_g} \right )
  \end{align*}
$$
Solving the quadratic form yields

$$
|\mathbf{V}|^2= \dfrac{1}{2} (V_g^2 - 2 \omega L Q - 2RP) \pm \sqrt{\left ( \frac{1}{2} (V_g^2 - 2 \omega L Q - 2RP)\right )^2 - |\mathbf{Z}|^2 (P^2+Q^2)}
$$

```{note}
The voltage expression has two solutions. The maximum amount of power that
can be transferred is found when the value under the square root vanishes, and the value of load voltage at that maximum point is simply calculated by what is outside of the square root.
```
The reactive power drawn by the load has a substantive impact on the voltage.
Inductive reactive power reduces voltage and maximum power transfer, while capacitive reactive power increases voltage and maximum power transfer. {numref}`vstab` shows an example for $\mathbf{V}_g = 12$ kV, $X = \omega L = 10\Omega$, $R = 1 \Omega$, and $Q = \pm 1$ MVAR.


```{figure} fig/AC/main-figure15.svg
---
name: vstab
width: 700px
align: center
---
Power circuit with a generalised reactive element.
```

## Summary

We reviewed the fundamental of AC circuits and instigated the relationship between complex power, real power, and reactive power. We briefly discussed the interplay of reactive power and voltage in form of voltage stability.
