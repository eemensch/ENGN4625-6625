# Principles of Steady-State Converter Analysis

Before we start our treatment of DC-DC converters, we need to be reacquainted to the notion of an _Ideal Switch_ and get familiarised with the type of ideal switches that help us with analysing converters.

__Single pole, single throw (SPST) Switch.__ A simple on-off switch.  

```{figure} fig/SPST.svg
---
width: 200px
---
An ideal SPST Switch
```

<!-- ![](fig/SPST.svg) -->

- Switch Closed: $v(t) = 0$.
- Switch Open: $i(t)=0$.
- $\forall t$: $\underbrace{p(t)}_{\text{Power}} =v(t) i(t) =0$.

__Single pole, double throw (SPDT) Switch.__ The common port is connected to either 1 or 2.


```{image} fig/SPDT.svg
:width: 200px
:align: center
```
<!-- ![](fig/SPDT.svg) -->

```{admonition} What is ideal about them?
:class: dropdown
They consume zero power. When they are off they block the current perfectly and when they conduct they have zero resistance (no voltage drop).

In practice we use semi-conductor devices (e.g., diodes and transistors) to realise these switches. Semi-conductor devices are desired to operate like this (loss-less).
```

## DC-DC Converter Example

In the circuit below, for $V_g=100\text{V}$ and $R=5\Omega$, design a converter such that $V=50\text{V}$, $I=10\text{A}$.

```{image} fig/dcdc_converter.svg
:width: 400px
:align: center
```
<!-- ![](fig/dcdc_converter.svg) -->

We investigate the following three designs:
- Resistive Voltage Divider (Dissipative realisation)
- Series Pass Regulator (Dissipative realisation)
- Use of an SPDT Switch


### Resistive Voltage Divider

A variable resistor in series with the load yields the following circuit.

<!-- ![](fig/divider.svg) -->

```{image} fig/divider.svg
:width: 500px
:align: center
```

### Series Pass Regulator

A series pass regulator (aka series voltage regulator) comprises of a transistor operating in the linear (aka ohmic, active) region.

<!-- ![](fig/linear_reg.svg) -->

```{image} fig/linear_reg.svg
:width: 500px
:align: center
```

### Use of an SPDT Switch

Using an SPDT switch changes the dc component of the input voltage. If we switch back and forth between on and off position in effect we ___chop___ the input voltage.

```{image} fig/proto_buck.svg
:width: 500px
:align: center
```
<!-- ![](fig/proto_buck.svg) -->

The switching duty cycle is denoted by $D$ where $0\leq D\leq 1$. We use $D'$ to denote its complement where $D'=1-D$. The switching period is represented by $T_s$ and consequently the switching frequency, $f_s=\dfrac{1}{T_s}$.

```{image} fig/duty2.svg
:width: 500px
:align: center
```
<!-- ![](fig/duty2.svg) -->

DC component ($\equiv$ average value):
$\begin{align*}
  \langle v_s \rangle = \dfrac{1}{T_s} \int_0^{T_s}  v_s(t)\mathrm{d}t = \dfrac{1}{T_s} (D T_s V_g) = D V_g
\end{align*}$

Computing the Fourier series of the periodic switching signal $v_s(t)$ yields

$$
\begin{align*}
  v_s(t) &=V_g \left [\dfrac{DT_s}{T_s}  +\sum_{n=1}^\infty \dfrac{2}{n\pi}\sin \left ( \dfrac{\pi n D T_s}{T_s}\right )\cos \left ( \dfrac{2\pi n }{T_s} \left (t-\dfrac{D T_s}{2} \right )\right )\right ]\\
  &=V_g \left [D  +\sum_{n=1}^\infty \dfrac{2}{n\pi}\sin \left ( \pi n D\right )\cos \left ( \dfrac{2\pi n }{T_s} \left (t-\dfrac{D T_s}{2} \right ) \right )\right ]\\
  <!-- \mathbf{v}_s(f) &= V_g \left [D\delta(f) +\sum_{n=1}^\infty \dfrac{2}{n\pi}\sin \left ( \pi n D\right ) \left ( \dfrac{\delta(f-n f_s)+\delta(f+n f_s)}{2}\right )\right ] -->
\end{align*}
$$

Consequently, its Fourier transform is

$$
\begin{align*}
  \mathbf{v}_s(f) &= V_g \left [D\delta(f) +\sum_{n=1}^\infty \dfrac{1}{n\pi}\sin \left ( \pi n D\right ) \left ({\delta(f-n f_s)+\delta(f+n f_s)}\right )\right ]
\end{align*}
$$

with the spectrum depicted below.

```{image} fig/FT.svg
:width: 600px
:align: center
```
<!-- ![](fig/FT.svg) -->


The magnitude of $n$-th harmonic is $ \dfrac{V_g}{n\pi} | \sin \left ( \pi n D\right ) |$. The effect of applying a low pass filter to remove switching harmonics and pass only the DC component is presented pictorially next.

```{image} fig/FT_fil.svg
:width: 600px
:align: center
```
<!-- ![](fig/FT_fil.svg) -->

To remove the switching harmonics one can implement the low-pass filter using $L$ and $C$ elements. Something that is known as an $L-C$ low-pass filter (and ideally is loss-less). Placing the filter in the circuit one obtains

```{figure} fig/buck_example.svg
---
width: 500px
---
Our first buck converter!
```

<!-- ![](fig/buck_example.svg) -->

The cutoff frequency of the the filter should be much smaller than the switching frequency $f_s$. The circuit is a ___buck converter___.

The relationship between the DC component of the output voltage $v$ and the input voltage $V_g$ is given by

$$
V \approx \langle v_s \rangle = DV_g
$$

This relationship is presented below.

<!-- ![](fig/buck_VD.svg) -->
```{figure} fig/buck_VD.svg
---
width: 300px
---
The graph of the conversion ratio of buck converter as a function of the duty cycle $D$.
```

In an ideal scenario, the relationship between the input and the (steady-state) DC value of the output, $V$ is a function of the duty cycle $D$ and can be written as

$$
V = M(D) V_g.
$$

In a buck converter $M(D)=D$.
<!-- Using a low-pass filter to remove switching harmonics and pass only the DC component:

![](fig/buck.svg)

Low-pass $LC$ filter cutoff frequency: $f_0$

Desired: $f_0\ll f_s$ -->







Three basic DC-DC converters of interest are:

- Buck converter
- Boost converter
- Buck-boost converter

The boost and buck-boost converters schematics realised using ideal switches are demonstrated in {numref}`boost` and {numref}`buckboost`, respectively.
Taking a route similar to what we took to analyse buck converters, that is using Fourier analysis and filtering, is full peril and will not take us far enough. In general, Fourier analysis along with low pass filter arguments are not always easy to apply to arbitrary converters. A systematic approach is required to analyse different circuits. Understanding and applying such an approach is the focus of this chapter.

```{figure} fig/boost.svg
---
width: 500px
name: boost
---
Boost converter with ideal switch
```

<!-- ![](fig/boost.svg) -->

```{figure} fig/buck_boost.svg
---
width: 500px
name: buckboost
---
 Buck-boost converter with ideal switch
```


<!-- ![](fig/buck_boost.svg) -->



## Inductor volt-second balance, capacitor charge balance, and the small ripple approximation

Consider the buck converter of {numref}`buck`.
```{figure} fig/buck.svg
---
width: 500px
name: buck
---
 Buck converter with ideal switch
```

<!-- ![](fig/buck.svg) -->

The actual output voltage waveform will not be exactly equal to a constant DC value and it will look like what is depicted in {numref}`act_wave`. Let's assume it takes the following form

$$
v(t)=V + v_{ripple}(t)
$$

For example, $V=1 \text{V}$, and the maximum of the additive ripple wave form is 10 mV, i.e., $\max |v_{ripple}(t)|=10 \text{mV}$.

```{figure} fig/act_wave.svg
---
width: 500px
name: act_wave
---
 A less-idealised representation of the output voltage waveform.
```

<!-- ![](fig/act_wave.svg) -->

In a well-designed converter, the output voltage ripple is much smaller than the DC component. Hence, the waveforms can be easily determined by ignoring the ripple:
$\|v_{ripple}(t)\|\ll V$
Hence, $v(t) \approx V$: small-ripple approximation

1. The small-ripple approximation is useful only for continuous waveforms. Particularly
- innductor currents
- capacitor voltages
2. Small-ripple approximation cannot be applied to discontinous signals (e.g.~pulsating waveforms that switch)
3. It is used to simplify the solutions to the ODEs describing the network. The small-ripple approximation let the solution to be calculated as linear functions. It is also known as the linear ripple approximation.
4. It is only valid when $T_s$ is short compared to the network time-constants.

(Relevant) Lame Joke of the Day
  Reality:
- An engineer thinks that equations are an approximation to reality.
- A physicist thinks reality is an approximation to equations.
- A mathematician doesn't care.

## Buck converter analysis

Let's revisit our trusty friend, the buck converter. In what follows we will go through the process of developing a systematic approach to analyse its behaviour at steady-state. To this aim we investigate the circuit for the two positions of the switch.
<!-- ![](fig/buck.svg) -->

__Switch in position 1:__

```{figure} fig/buck_sw1.svg
---
width: 500px
name: buck_sw1
---
The buck converter circuit when the switch is in position 1.
```

<!-- ![](fig/buck_sw1.svg) -->

- Inductor voltage: $v_L = V_g -v(t)$
- Small ripple approximation: $v_L \approx V_g- V$
- Inductor current: $v_L(t) = L\dfrac{di_L(t)}{\mathrm{d}t}$
- Variation of current (the slope):

$$
\dfrac{di_L(t)}{\mathrm{d}t}=\dfrac{v_L(t)}{L}\approx\dfrac{V_g - V}{L}
$$


```{attention}
The inductor current changes with a constant slope.
```

__Switch in position 2:__

<!-- ![](fig/buck_sw2.svg) -->
```{figure} fig/buck_sw2.svg
---
width: 500px
name: buck_sw2
---
The buck converter circuit when the switch is in position 2.
```

- Inductor voltage: $v_L = -v(t)$
- Small ripple approximation: $v_L \approx - V$
- Inductor current: $v_L(t) = L\dfrac{di_L(t)}{\mathrm{d}t}$
- Variation of current (the slope): $\dfrac{di_L(t)}{\mathrm{d}t}\approx\dfrac{- V}{L}$


```{attention}
The inductor current changes with a constant slope.
```

### Inductor voltage and current waveforms

Now, let's see how the voltage across the two terminals of the inductor behaves over a switching period. From the equations above we can depict the wave-form as below.

<!-- ```{image} fig/vL_buck.svg
:width: 500px
:align: center -->
<!-- ``` -->

```{figure} fig/vL_buck.svg
---
width: 500px
name: vL_buck
---
The inductor voltage waveform in a buck converter.
```

<!-- ![](fig/vL_buck.svg) -->
Remember that the relationship between the current through and an inductor and its voltage is

$$L\dfrac{\mathrm{d}i}{\mathrm{d}t} = v.$$

In other words, the _slope_ of the current waveform is given by $v/L$. From this observation:

$$
\begin{align*}\dfrac{di_L(t)}{\mathrm{d}t}&=\dfrac{v_L(t)}{L} \approx \begin{cases}
\frac{V_g-V}{L} & \text{Position 1}\\
\frac{-V}{L} & \text{Position 2}
\end{cases}\end{align*}
$$

The current waveform is depicted below.

<!-- ```{image} fig/il_buck.svg
:width: 500px
:align: center
``` -->

```{figure} fig/il_buck.svg
---
width: 500px
name: iL_buck
---
The inductor current waveform in a buck converter.
```

<!-- ![](fig/il_buck.svg) -->
```{note}
In practice the ripple is set to be around 10-20 percent of the DC value.
```

### Determination of inductor current ripple magnitude


<!-- ![](fig/il_buck.svg) -->

The total, _peak-to-peak_ change in $i_L$ as observable from {numref}`iL_buck` in each sub-interval is

$$
2\Delta i_L = \left ( \dfrac{V_g-V}{L} \right) DT_s
$$
Equivalently, the peak-to-average ripple (half of the peak-to-peak ripple) is

$$
\Delta i_L = \left ( \dfrac{V_g-V}{2L} \right) DT_s \quad \iff \quad L = \left ( \dfrac{V_g-V}{2\Delta i_L} \right) DT_s
$$

This relationship can be used to select the appropriate magnitude of $L$ to achieve a certain ripple.

### Inductor current waveform during turn-on transient

Inductor current waveform during turn-on transient:

![](fig/il_trans_buck.svg)

Converter in equilibrium: $i_L((n+1)T_s)=i_L(nT_s)$

### Numerical solution for $i_L(t)$ and $v(t)$ using a circuit simulator

![](fig/num_iL_buck.svg)

![](fig/num_v_buck.svg)



- $C=22 \mu\text{F}$, $L=\text{mH}$, $R=15\Omega$, $V_g=10\text{V}$, $T_s=20\mu \text{s}$, $D=0.75$.
- Note that the waveforms are made up of line segments.
- Ripple after $5 \text{ms}$: 0.01850875. Expected ripple at steady state: $\Delta i_L = \dfrac{V_g-V}{2L}DT_s=0.01875$.

## The principles of inductor volt-second balance and capacitor charge balance

### The principle of inductor volt-second balance

Inductor defining relation: $v_L = L \dfrac{\mathrm{d} i_L(t)}{\mathrm{d}t}$

Integrating the current over one switching period results in

$$
i_L(T_s) - i_L(0) = \dfrac{1}{L} \int_0^{T_s} v_L(t) \mathrm{d}t
$$

In periodic steady state, that is, when the transients have settled down and the converter is in equilibrium, the net change in inductor current is zero:

$$
0 = \dfrac{1}{T_s} \int_0^{T_s} v_L(t) \mathrm{d}t
$$
Hence, the total area (or _volt-second_) under the inductor voltage waveform is zero whenever the converter operates in steady state.

```{admonition} Inductor volt-second balance
The average inductor voltage is zero in steady state.

$$
0 = \dfrac{1}{T_s} \int_0^{T_s} v_L(t) \mathrm{d}t = \langle v_L \rangle
$$
```


#### Inductor volt-second balance in buck converters

The integral of the voltage waveform (see {numref}`vL_buck`) is the area of rectangles:

$$
\int_0^{T_s} v_L(t) \mathrm{d}t =  (V_g-V)(DT_s) + (-V)(D'T_s)
$$

<!-- ![](fig/vL_buck.svg) -->

The average voltage is

$$
 \langle v_L \rangle = \dfrac{1}{T_s}\int_0^{T_s} v_L(t) \mathrm{d}t = D(V_g-V) +D' (-V)
$$

After applying the inductor volt-second balance principle, i.e.~equating the average value to zero and solving for $V$ yields

$$
0 = DV_g -(D+D') V = DV_g -V \implies V = D V_g
$$


### The principle of capacitor charge balance

The capacitor defining relation is $i_C(t) = C \dfrac{\mathrm{d}v_C(t)}{\mathrm{d}t}$
Integrating over one switching period:

$$
v_C(T_s) - v_C(0) = \dfrac{1}{C} \int_0^{T_s} i_C(t) \mathrm{d}t
$$
As above, in preiodic steady state, the net change in capacitor voltage is zero:

$$
0 = \dfrac{1}{T_s} \int_0^{T_s} i_C(t) \mathrm{d}t
$$
Hence, the total area (or _charge_) under the capacitor current waveform is zero whenever the converter operates in steady state.

```{admonition} Capacitor charge balance
The average capacitor current is zero in steady state.

$$
0 = \dfrac{1}{T_s} \int_0^{T_s} i_C(t) \mathrm{d}t = \langle i_C \rangle
$$
```

```{warning}
We have to be careful when we talk about charging a capacitor and a capacitor charge. There is a fundamental misunderstanding in thinking about capacitors as a place to store electric charge. We really store energy in a capacitor. A good discussion can be found [here](http://amasci.com/emotor/cap1.html). Please note that this discussion has no impact on how we use the principle of charge balance to study the behaviour of converters.  
```

## Boost Converter Analysis

Consider the Boost converter with ideal switch of {numref}`boost`. As we will see in future chapters this circuit can be realised in practice with
a power transistor and a (free-wheeling) diode. The practical circuit realisation is presented in {numref}`boost_prac`.

```{figure} fig/boost_physical.svg
---
width: 500px
name: boost_prac
---
A practical realisation of the boost converter
```

<!-- ![](fig/boost_physical.svg) -->


__Switch in position 1:__

<!-- ![](fig/boost_sw1.svg) -->

```{figure} fig/boost_sw1.svg
---
width: 500px
name: boost_sw1
---
The boost converter circuit when the switch is in position 1.
```


The inductor voltage and capacitor current are

$$
v_L = V_g, \quad i_C=-v/R
$$

After applying the small ripple approximation one obtains the following relationships:

$$
v_L \approx V_g, \quad i_C \approx -V/R
$$
__Switch in position 2:__

```{figure} fig/boost_sw2.svg
---
width: 500px
name: boost_sw2
---
The boost converter circuit when the switch is in position 2.
```

In this case the inductor voltage and capacitor current are

$$
v_L = V_g - v, \quad i_C=i_L-v/R
$$

Again, applying the small ripple approximation results in

$$
v_L \approx V_g-V, \quad i_C\approx I-V/R
$$


### Inductor volt-second balance in boost converters

<!-- ![](fig/vL_boost.svg) -->

<!-- ``{image} fig/il_buck.svg
:width: 500px
:align: center -->
<!-- ``` -->

```{figure} fig/vL_boost.svg
---
width: 500px
name: vL_boost
---
The inductor voltage waveform in a boost converter.
```

From the volt-seconds balance principle applied to inductor:

$$
\begin{align*}
     0&=\int_0^{T_s} v_L(t) \mathrm{d}t= V_g D T_s + (V_g-V) D'T_s\\
     0&=V_g(D+D') -V D' \implies V=\dfrac{V_g}{D'}
\end{align*}
$$

Solving the algebraic equation above, one obtains the voltage conversion ratio as

$$
M(D) =\dfrac{V}{V_g} = \dfrac{1}{D'}=\dfrac{1}{1-D}
$$

### Conversion ratio of the boost converter $M(D)$

The conversion ratio of the boost converter as the function of the duty cycle is depicted in {numref}`MD_boost` and is given below:

$$
M(D)=\dfrac{V}{V_g}=\dfrac{1}{D'}=\dfrac{1}{1-D}
$$

<!-- ![](fig/MD_boost.svg) -->
```{figure} fig/MD_boost.svg
---
width: 300px
name: MD_boost
---
The graph of the conversion ratio of boost converter as a function of the duty cycle $D$.
```



```{note}
  The ideal conversion rate goes to infinity. But real converters cannot achieve that. In fact, the maximum output of a converter is limited by the losses (we will study losses in the future.)
```

### Capacitor charge balance in boost converters

The waveform of the capacitor current in a boost converter is presented below:

<!-- ![](fig/iC_boost.svg) -->

```{figure} fig/iC_boost.svg
---
width: 500px
name: iC_boost
---
The capacitor current waveform in a boost converter.
```

Net charge applied to the capacitor over one period:

$$
  \begin{align*}
     0&=\int_0^{T_s} i_C(t) \mathrm{d}t= (-V/R) D T_s +(I-V/R)D'T_s\\
     0&=-V/R(D+D') -I D' \implies \\
     I &=\dfrac{V}{D'R} \implies I = \dfrac{V_g}{D'^2 R}
   \end{align*}
$$

### Determination of inductor current ripple in boost converters

From the inductors defining relationship and in light of the voltage waveform of an inductor one can write

$$
\begin{align*}\dfrac{di_L(t)}{\mathrm{d}t}&=\dfrac{v_L(t)}{L} \approx \begin{cases}
      \frac{V_g}{L} & \text{Position 1}\\
\frac{V_g-V}{L} & \text{Position 2}
\end{cases}\end{align*}
$$
The waveform is depicted in {numref}`il_boost`.

```{figure} fig/il_buck.svg
---
width: 500px
name: iL_boost
---
The inductor current waveform in a boost converter.
```
<!-- ![](fig/il_buck.svg) -->



The peak-to-peak change in inductor current during subinterval 1:

$$
2 \Delta i_L = \dfrac{V_g}{L} D T_s \iff   \Delta i_L = \dfrac{V_g}{2L} DT_s
$$

One may choose $L$ for a desired ripple magnitude given other circuit parameters.


### Determination of capacitor voltage ripple in boost converters
Using the defining equation for capacitors:

$$
  \begin{align*}\dfrac{dv_C(t)}{\mathrm{d}t}&=\dfrac{i_C(t)}{C} \approx \begin{cases}
      \frac{-V}{RC} & \text{Position 1}\\
\dfrac{I}{C}-\frac{V}{RC} & \text{Position 2}
\end{cases}\end{align*}
$$

The capacitor voltage waveform is presented in {numref}`vC_boost`.

```{figure} fig/vC_boost.svg
---
width: 500px
name: vC_boost
---
The capacitor voltage waveform in a boost converter.
```
<!-- ![](fig/vC_boost.svg) -->

The peak-to-peak change in capacitor voltage during subinterval 1 is described by

$$
 -2 \Delta v = -\dfrac{V}{RC} D T_s \iff   \Delta v = \dfrac{V}{2RC} D T_s
$$

As before, one can choose $C$ for a desired ripple magnitude.
In practice, capacitor equivalent series resistance (esr) leads to increased voltage ripple.

## &Cacute;uk (pronounced chook) converter analysis


A &Cacute;uk converter with ideal switch is presented in {numref}`cuk`. The practical implementation of the circuit using transistors and diodes is given in {numref}`cuk_prac`.

```{figure} fig/cuk.svg
---
width: 500px
name: cuk
---
&Cacute;uk converter with ideal switches
```

<!-- ![](fig/cuk.svg) -->

```{figure} fig/cuk_physical.svg
---
width: 500px
name: cuk_prac
---
&Cacute;uk converter practical realisation using power transistor and diode
```


<!-- ![](fig/cuk_physical.svg) -->

__Switch in position 1:__ When the switch is in position 1, the transistor conducts currents and $C_1$ releases energy to the output. The equivalent circuit for this case is depicted below.

```{figure} fig/cuk_sw1.svg
---
width: 500px
name: cuk_sw1
---
The &Cacute;uk converter circuit when the switch is in position 1.
```
<!-- ![](fig/cuk_sw1.svg) -->

Inductor voltages and capacitor currents are

$$
\begin{aligned}
  v_{L1} &= V_g,\\
  v_{L2} &= -v_1 -v_2,\\
  i_{C1} &= i_2,\\
  i_{C2} &= i_2-\dfrac{v_2}{R}
\end{aligned}
$$

Applying the small ripple approximation gives

$$
\begin{aligned}
  v_{L1} = V_g.\\
  v_{L2} = -V_1 -V_2,\\
  i_{C1} = I_2,\\
  i_{C2} = I_2-\dfrac{V_2}{R}
\end{aligned}
$$

__Switch in position 2:__ In this case the diode conducts, and capacitor $C_1$ is charged from the input. This circuit configuration for this case is presented below.


```{figure} fig/cuk_sw2.svg
---
width: 500px
name: cuk_sw2
---
The &Cacute;uk converter circuit when the switch is in position 2.
```
<!-- ![](fig/cuk_sw2.svg) -->


Inductor voltages and capacitor currents:

$$
\begin{aligned}
  v_{L1} &= V_g-v_1,\\
  v_{L2} &=  -v_2,\\
  i_{C1} &= i_1,\\
  i_{C2} &= i_2-\dfrac{v_2}{R}
\end{aligned}
$$

Small ripple approximation:

$$
\begin{aligned}
  v_{L1} &= V_g-V_1,\\
  v_{L2} &= -V_2,\\
  i_{C1} &= I_1,\\
  i_{C2} &= I_2-\dfrac{V_2}{R}
\end{aligned}
$$

The principles of inductor volt-second and capacitor charge balance state that ___the average values of the periodic inductor voltage and capacitor current waveforms are zero___, when the converter operates in steady state. Hence, to determine the steady-state conditions in the converter, sketch the inductor voltage and capacitor current waveforms, and equate their average values to zero.

The waveforms of the voltages of $L_1$ and $L_2$ are presented in {numref}`vL1_cuk` and {numref}`vL2_cuk`, respectively.

```{figure} fig/vL1_cuk.svg
---
width: 500px
name: vL1_cuk
---
$L_1$ voltage waveform in {ref}`cuk`
```

```{figure} fig/vL2_cuk.svg
---
width: 500px
name: vL2_cuk
---
$L_2$ voltage waveform in {ref}`cuk`
```

The volt-second balance principle applied to $L_1$ and $L_2$ give

$$
\langle v_{L1} \rangle = DV_g+D'(V_g-V_1)=0
$$

<!-- ![](fig/vL1_cuk.svg) -->


$$
\langle v_{L2} \rangle = D(-V_1-V_2)+D'(-V_2)=0
$$

<!-- ![](fig/vL2_cuk.svg) -->

The waveforms of the currents of $C_1$ and $C_2$ are presented in {numref}`iC1_cuk` and {numref}`iC2_cuk`, respectively.

```{figure} fig/iC1_cuk.svg
---
width: 500px
name: iC1_cuk
---
$C_1$ current waveform in {ref}`cuk`
```

```{figure} fig/iC2_cuk.svg
---
width: 500px
name: iC2_cuk
---
$C_2$ current waveform in {ref}`cuk`
```

Applying the charge balance principle to $C_1$ and $C_2$ results in

$$
\langle i_{C1} \rangle = DI_2+D'I_1=0
$$

<!-- ![](fig/iC1_cuk.svg) -->

$$
\langle i_{C2} \rangle = I_2-\dfrac{V_2}{R}=0
$$
<!-- ![](fig/iC2_cuk.svg) -->

During both switch positions, the capacitor current $i_{C2}$ is equal to the difference between the inductor current $i_2$ and the load current $V_2/R$. When the ripple is neglected, $i_{C2}$ is constant and equal to zero.

The conversion ratio of a &Cacute;uk converter is

$$
M(D) = \dfrac{V_2}{V_g}= - \dfrac{D}{1-D}
$$
Its graph in term of the duty cucle $D$ is depicted below.

```{figure} fig/cuk_MD.svg
---
width: 300px
name: MD_cuk
---
The graph of the conversion ratio of &Cacute;uk converter as a function of the duty cycle $D$.
```
<!-- ![](fig/cuk_MD.svg) -->

### Determination of $L_1$ and $L_2$ currents ripples

Using the defining equation for inductors $L_1$ and $L_2$ and given their voltages over a switching interval we obtain

$$
\begin{align*}\dfrac{di_1(t)}{\mathrm{d}t}&=\dfrac{v_{L1}(t)}{L} \approx \begin{cases}
        \frac{V_g}{L_1} & \text{Position 1}\\
  \frac{V_g-V_1}{L_1} & \text{Position 2}
  \end{cases}
\end{align*}
$$

![](fig/iL1_ripple.svg)

$$
\begin{align*}
\dfrac{di_2(t)}{\mathrm{d}t}&=\dfrac{v_{L2}(t)}{L}\approx \begin{cases}
      \frac{-V_1-V_2}{L_2} & \text{Position 1}\\
\frac{-V_2}{L_2} & \text{Position 2}
\end{cases}\end{align*}
$$

The corresponding currents waveforms are given below.

```{figure} fig/iL1_ripple.svg
---
width: 500px
name: iL1_cuk
---
$L_1$ current waveform in {ref}`cuk`
```

```{figure} fig/iL2_ripple.svg
---
width: 500px
name: iL2_cuk
---
$L_2$ current waveform in {ref}`cuk`
```

<!-- ![](fig/iL2_ripple.svg) -->

### Determination of $C_1$ and $C_2$ voltages ripples

Applying the capacitor defining relationship to $C_1$ and given its voltage waveform, one obtains

$$
\begin{align*}\dfrac{dv_1(t)}{\mathrm{d}t}&=\dfrac{i_{C1}(t)}{C_1}\approx \begin{cases}
        \frac{I_2}{C_1} & \text{Position 1}\\
  \frac{I_1}{C_1} & \text{Position 2}
  \end{cases}\end{align*}
$$

```{figure} fig/vC1_ripple.svg
---
width: 500px
name: vC1_cuk
---
$C_1$ voltage waveform in {ref}`cuk`
```
<!-- ![](fig/vC1_ripple.svg) -->

Doing the same to $C_2$ yields
$$
\dfrac{dv_2(t)}{\mathrm{d}t}=\dfrac{i_{C2}(t)}{L}\approx 0 ???
$$

```{error}
This is weird! Of course there is ripple in the waveform. The small ripple approximation does not explain everything here. We need a better approximation.
```

## Estimating ripple in converters containing two-pole low-pass filters (e.g. Buck and &Cacute;uk)


Consider the circuit with an output two-pole filter as shown below.

```{image} fig/two_pole.svg
:width: 500px
:align: center
```

<!-- ![](fig/two_pole.svg) -->

The inductor current waveform is given below

```{image} fig/iL_ripple.svg
:width: 500px
:align: center
```

<!-- ![](fig/iL_ripple.svg) -->

What is the capacitor current?

```{figure} fig/total_charge.svg
---
width: 500px
name: total_charge
---
The total charge in the capacitor.
```

<!-- ![](fig/total_charge.svg) -->

If the capacitor voltage ripple is small, then essentially all of the ac component of inductor current flows through the capacitor. The inductor current ripple must not be neglected.


the current $i_C(t)$ is positive for half of the switching period. This positive current causes the capacitor voltage $v_C(t)$ to increase between its minimum and maximum extrema. During this time, the total charge $q$ is deposited on the capacitor plates, where

$$
q = C (2\Delta v)
$$

The total charge $q$ is the area of the triangle, as shown

$$
q = \dfrac{1}{2} \Delta i_L \dfrac{T_s}{2}
$$

Having $q = C (2\Delta v)$ and solving for $\Delta v$:

$$
\Delta v = \dfrac{\Delta i_L T_s}{ 8C}
$$

In practice, capacitor equivalent series resistance (esr) further increases the ripple, $\Delta v$.

Summary:

$$
\begin{array}{cc}
    \Delta i_1 = \dfrac{V_g D T_s}{2L_1},  &\Delta i_2 = \dfrac{V_1+V_2}{2L_2}D T_s = \dfrac{V_g}{2L_2}D T_s\\
    \Delta v_1 = \dfrac{-I_2 D T_s}{ 2C_1}= \dfrac{V_g D^2 T_s }{2 D' RC_1}, &\Delta v_2 = \dfrac{V_g D T_s^2}{ 16C_2 L_2}
    \end{array}
$$

### Inductor current ripple in two-pole filters

Now consider a circuit with an input two-pole filter as shown in the following figure.

```{image} fig/input_filter.svg
:width: 500px
:align: center
```

<!-- ![](fig/iL_ripple.svg) -->



<!-- ![](fig/input_filter.svg) -->

```{figure} fig/total_flux.svg
---
width: 500px
name: total_flux
---
The total flux in the inductor.
```
<!-- ![](fig/total_flux.svg) -->

The total linkage flux $\lambda$ is the area of the triangle, as shown

$$
\lambda = \dfrac{1}{2} \Delta v \dfrac{T_s}{2}
$$

Letting $\lambda = L (2\Delta i_L)$ and solving for $\Delta i_L$:

$$
\Delta i_L = \dfrac{\Delta v T_s}{ 8L}
$$
As mentioned before inductor linkage flux is the same as its volt-seconds.

## Summary

The dc component of a converter waveform is given by its average value, or the integral over one switching period, divided by the switching period. Solution of a dc-dc converter to find its dc, or steady-state, voltages and currents therefore involves averaging the waveforms.

 The linear ripple approximation greatly simplifies the analysis. In a well-designed converter, the switching ripples in the inductor currents and capacitor voltages are small compared to the respective dc components, and can be neglected.

 The principle of inductor volt-second balance allows determination of the dc voltage components in any switching converter. In steady-state, the average voltage applied to an inductor must be zero.

 The principle of capacitor charge balance allows determination of the dc components of the inductor currents in a switching converter. In steady-state, the average current applied to a capacitor must be zero.

By knowledge of the slopes of the inductor current and capacitor voltage waveforms, the ac switching ripple magnitudes may be computed. Inductance and capacitance values can then be chosen to obtain desired ripple magnitudes.

In converters containing multiple-pole filters, continuous (nonpulsating) voltages and currents are applied to one or more of the inductors or capacitors. Computation of the ac switching ripple in these elements can be done using capacitor charge and/or inductor flux-linkage arguments, without use of the small-ripple approximation.

Converters capable of increasing (boost), decreasing (buck), and inverting the voltage polarity (buck-boost and &Cacute;uk) have been described. Converter circuits are explored more fully in future.
