# Equivalent Circuit Model of Steady-State Converter

The first ingredient of am equivalent circuit model is the _DC Transformer_.

## DC Transformer Model

For an ideal converter with efficienct $\eta =100 \%$:

$$
P_{in}=P_{out}, \quad V_g I_g = V I
$$
Thus, the ideal conversion ratio becomes:

$$
V=M(D) V_g, \quad I_g = M(D) I
$$

```{figure} fig/switchingdcdc.svg
---
width: 500px
---
Schematic of a converter.
```

These equations are valid in steady-state. During transients, energy storage within filter elements may cause $P_{in}\neq P_{out}$.

$$
P_{in}=P_{out}, \quad V_g I_g = V I,\quad V=M(D) V_g,  \quad I_g = M(D) I
$$ (ideal)
An equivalent circuit that satisfies these equations is given below.

```{figure} fig/DepSourceDCTrans.svg
---
width: 400px
name: dep_source_dc_trans
---
A circuit with dependant sources that satisfy  {eq}`ideal`.
```

This equivalent circuit can in turn be represented with the DC transformer equivalent element as depicted below.

```{figure} fig/DCTrans.svg
---
width: 400px
name: DCTrans
---
The DC transformer element equivalen to {numref}`dep_source_dc_trans`. Note the thick horizontal bar to remind ourself that this DC ``transformer'' is just a model.
```

### Transformer Review

A multiple winding transformer is given below.

```{figure} fig/transformer.svg
---
width: 400px
name: multi_trans
---
A general multi-port transformer.
```
$$
\dfrac{v_1(t)}{n_1}=\dfrac{v_2(t)}{n_2}=\dfrac{v_3(t)}{n_3}
$$

$$
n_1 i_1(t)+n_2i_2(t) +n_3 i_3(t)=0
$$
One can reflect elements through the windings of a transformer to construct equivalent circuits.

The reflection of a voltage source, a current source, and an impedance through a transformer are presented below.

```{image} fig/v_reflect.svg
:width: 400px
:align: center
```
```{image} fig/i_reflect.svg
:width: 400px
:align: center
```
```{image} fig/z_reflect.svg
:width: 400px
:align: center
```

Similarly, one can reflect voltage sources, current sources, and impedances through a DC transformer model and arrive at equivalent circuits.

```{image} fig/dc_v_reflect.svg
:width: 400px
:align: center
```
```{image} fig/dc_i_reflect.svg
:width: 400px
:align: center
```
```{image} fig/dc_z_reflect.svg
:width: 400px
:align: center
```
An ideal DC transfoemr would conversion  DC voltages and currents with 100\% efficiency where the conversion ratio $M(D)$ controllable via the duty cycle.

```{figure} fig/dc_trans_d.svg
---
width: 400px
---
The choice of the duty cycle $D$ changes the turn-ratio in a DC transformer model.
```
In the schematic, the solid line denotes ideal transformer model, capable of passing DC voltages and currents. This leads to a time-invariant model (no switching) which can be solved to find DC components of converter waveforms and simplifies the analysis.

### An example of application of the DC transformer model

Consider the case where an input voltage source of $V_1$ with a resistance equal to $R_1$ is connected to an ideal buck converter. What is the relationship between the output voltage and the input voltage?

The circuit corresponding to this scenario is depicted below.

```{image} fig/R1_circuit.svg
:width: 400px
:align: center
```

Reflecting $R_1$ through the DC transformer leads to:
```{image} fig/R1_reflected.svg
:width: 400px
:align: center
```
Solving the resulting circuit results in the relationship of interest:

$$
V = M(D) V_1 \dfrac{R}{R+M^2(D)R_1}
$$
### Converter analysis in the presence of inductor copper loss

The DC transformer model can be extended to include converter nonidealities, in this case the copper loss of the inductor.

The equivalent circuit of an inductor with some opper loss modelled as a resistance $R_L$ is given below.

```{image} fig/L_copper.svg
:width: 200px
:align: center
```
A boost converter with this lossy inductor would look like:
```{image} fig/lossy_L_boost.svg
:width: 400px
:align: center
```
Let's consider the behaviour of the converter when the switch is in positions 1 and 2.

__Switch in position 1:__

```{figure} fig/lossy_boost_sw1.svg
---
width: 500px
name: lossy_boost_sw1
---
The boost converter circuit with a lossy inductor when the switch is in position 1.
```

- Inductor voltage: $v_L = V_g - iR_L$
- Capacitor current:  $i_C=-v/R$
- Small ripple approximation:

$$
v_L \approx V_g - I R_L, \quad i_C \approx -V/R
$$

__Switch in position 2:__

```{figure} fig/lossy_boost_sw2.svg
---
width: 500px
name: lossy_boost_sw2
---
The boost converter circuit with a lossy inductor when the switch is in position 2.
```

- Inductor voltage: $v_L = V_g - iR_L-v$
- Capacitor current:  $i_C=i-v/R$
- Small ripple approximation:
$$
v_L \approx V_g-IR_L-V, \quad i_C \approx I-V/R
$$
```{figure} fig/vL_boost_lossy.svg
---
width: 500px
name: vL_boost_lossy
---
The voltage waveform of the inductor.
```

Inductor volt-seconds balance in light of {numref}`vL_boost_lossy` is written as

$$
\begin{aligned}
     \langle v_L\rangle &= (V_g-IR_L) D  + (V_g-IR_L-V) D'=0\\
     0&=V_g -IR_L-D'V.
\end{aligned}
$$
```{figure} fig/iC_boost.svg
---
width: 500px
name: iC_boost_lossy
---
The current waveform of the capacitor.
```
From {numref}`iC_boost_lossy`, the capacitor charge balance yields

$$
\begin{aligned}
\langle i_C\rangle &=D(-V/R) +D' (I-V/R)=0\\
0&= D' I -V/R.
\end{aligned}
$$
Thus,

$$
M(D) = \dfrac{V}{V_g}=\dfrac{1}{D'} \dfrac{1}{(1+R_L/(RD'^2) )}
$$
For different ratios of $\dfrac{R_L}{R}$, the conversion ratio $M(D)$ for the lossy boost converter of this example is depicted below.

```{figure} fig/BoostLossyMD.svg
---
width: 500px
name: BoostLossyMD
---
$M(D)$ for different $\dfrac{R_L}{R}$.
```

## Equivalent circuit model of converters

In the first example to illustrate the method we consider the setting of a boost converter with a lossy inductor, then we construct the equivalent circuit model of a book converter with a lossy inductor, and finally, we study the effect of semiconductor losses.

### Equivalent circuit model of a boost converter with lossy $L$

We use the setting of the last example. Remember:

$$
\begin{aligned}
    \langle v_L\rangle &=    0=V_g -IR_L-D'V\\
     \langle i_C\rangle &= 0 = D' I -V/R
\end{aligned}
$$ (lossy_boost_eq)

These can be seen as loop and node equations for some circuit. The question is how to reconstruct this circuit?

Note that the first equation is a loop equation obtained from the application of the Kirchoff's voltage law: the dc components of voltage around a loop containing the inductor sum to zero. A circuit of the following form satisfies the equation

```{figure} fig/Loop_boost.svg
---
width: 300px
name: Loop_boost
---
A circuit satisfying $\langle v_L\rangle =    0=V_g -IR_L-D'V$.
```

The second equation corresponds to a node equation obtained from the application of the Kirchoff's current law: the dc components of current flowing into a node connected to the capacitor sum to zero.

```{figure} fig/node_boost.svg
---
width: 300px
name: node_boost
---
A circuit satisfying $\langle i_C\rangle = 0 = D' I -V/R$.
```
Putting these two circuits side-by-side:

```{figure} fig/boost_equiv_circ.svg
---
width: 500px
name: boost_equiv_circ
---
An equivalent circuit with dependent sources that satisfy {eq}`lossy_boost_eq`.
```

Similar to {numref}`dep_source_dc_trans` and {numref}`DCTrans`, the dependent sources can be modelled as a  $D' : 1$ DC transformer:

```{figure} fig/equiv_boost_dctrans.svg
---
width: 500px
name: equiv_boost_dctrans
---
An equivalent circuit with a DC transformer element that satisfies {eq}`lossy_boost_eq`.
```
Pushing the elements through the transformer results in

```{image} fig/lossy_boost_reflected.svg
:width: 200px
:align: center
```
Output voltage:

$$
V = \dfrac{V_g}{D'}\dfrac{R}{R+\dfrac{R_L}{D'^2}}
$$

Input current:

$$
I = \dfrac{V_g}{D'^2 R+R_L}
$$


The converter efficiency is

$$
\begin{aligned}
\eta &= \dfrac{P_{out}}{P_{in}}= \dfrac{V (D'I)}{V_g I}=\dfrac{V}{V_g}D'=\dfrac{R}{R+\dfrac{R_L}{D'^2}}\\
    \eta &=\dfrac{1}{1+\dfrac{R_L}{D'^2 R}}
\end{aligned}
$$

Efficiency curves as a function of the duty cycle $D$ for different $\dfrac{R_L}{R}$ is given below.

```{image} fig/lossy_boostefficiency.svg
:width: 500px
:align: center
```
### Equivalent circuit model of a buck converter with lossy $L$

A buck converter with this lossy inductor would look like:
```{image} fig/lossy_buck.svg
:width: 400px
:align: center
```
Siimilar to the case of the boost converter studying the behaviour of the converter when the switch is in positions 1 and 2, and applying the small ripple approximation results in

$$
\langle v_L \rangle =0 =DV_g -I_L R_L -V_C,\quad \langle i_C \rangle =0=I_L -V_C/R.
$$

These two equations lead to the following circuit:

```{image} fig/buck_loop.svg
:width: 400px
:align: center
```

```{admonition} How should we obtain the rest of the circuit/transformer?
:class: dropdown
We have to find the __input port__ of the converter.
```
Input current waveform $i_g(t)$:

```{image} fig/input_port_buck.svg
:width: 400px
:align: center
```
The DC component (average value) of $i_g(t)$ is computed as

$$
I_g=\dfrac{1}{T_s}\int_0^{T_s} i_g(t) dt = DI_L
$$
The following circuit satisfies this node equation:

```{image} fig/buck_node.svg
:width: 100px
:align: center
```

Putting the two parts side-by-side, we obtain

```{image} fig/buck_sidebyside.svg
:width: 600px
:align: center
```

The dependent sources are equivalent to a $1 : D$ transformer, and the equivalent circuit becomes:

```{image} fig/buck_equiv_dc.svg
:width: 400px
:align: center
```
### Equivalent circuit model of a boost converter in the presence of semi-conductor conduction losses

The practical implementation of a boost converter is given below (we will learn about how to realise these devices using semiconductor devices later.)

```{image} fig/boost_semi.svg
:width: 400px
:align: center
```
We assume that the conduction losses of the semi-conductor devices in their on-state are modelled as the following:

- MOSFET: on-resistance $R_{on}$
- Diode: constant forward voltage $V_D$ and on-resistance $R_D$

Let's consider the behaviour of the converter when the switch is in positions 1 and 2.

__Switch in position 1:__

```{figure} fig/boost_semi_sw1.svg
---
width: 500px
name: boost_semi_sw1
---
The boost converter circuit with a lossy inductor when the switch is in position 1.
```

- Inductor voltage: $v_L = V_g - iR_L-iR_{on}$
- Capacitor current:  $ i_C= -v/R $
- Small ripple approximation:

$$
v_L \approx V_g - I R_L-IR_{on}, \quad i_C \approx -V/R
$$

__Switch in position 2:__

```{figure} fig/boost_semi_sw2.svg
---
width: 500px
name: boost_semi_sw2
---
The boost converter circuit with a lossy inductor when the switch is in position 2.
```

- Inductor voltage: $v_L = V_g - iR_L-V_D-iR_D-v$
- Capacitor current:  $i_C=i-v/R$
- Small ripple approximation:

$$
v_L \approx V_g-IR_L-V_D-IR_{D}-V, \quad i_C\approx I-V/R
$$
```{figure} fig/vL_boost_semi.svg
---
width: 500px
name: vL_boost_semi
---
The voltage waveform of the inductor.
```

Inductor volt-seconds balance in light of {numref}`vL_boost_semi` is written as

$$
\begin{aligned}
     \langle v_L\rangle &= (V_g-IR_L-IR_{on}) D  + (V_g-IR_L-V_D-IR_D-V) D'=0\\
     &=V_g -IR_L -IDR_{on} -D'V_D -ID'R_D -D'V=0.
\end{aligned}
$$
```{figure} fig/iC_boost.svg
---
width: 500px
name: iC_boost_semi
---
The current waveform of the capacitor.
```
From {numref}`iC_boost_semi`, the capacitor charge balance yields

$$
\begin{aligned}
\langle i_C\rangle &=D(-V/R) +D' (I-V/R)=0\\
      &= D' I -V/R=0.
\end{aligned}
$$

The following circuit satsifies the loop equation:

$$
V_g -IR_L -I DR_{on} -D'V_D -ID'R_D -D'V =0
$$

```{image} fig/boost_semi_loop.svg
:width: 400px
:align: center
```
The following circuit satsifies the node equation:

$$
D'I - V/R = 0
$$

```{image} fig/boost_semi_node.svg
:width: 100px
:align: center
```

Putting the two parts side-by-side one obtains

```{image} fig/boost_semi_sidebyside.svg
:width: 600px
:align: center
```

Replacing the dependance sources with a dc transformer yields the desired equivalent circuit:

```{image} fig/boost_semi_dctrans_equiv.svg
:width: 600px
:align: center
```

Solving the circuit for the output voltage, one obtains

$$
V = \dfrac{1}{D'} (V_g-D'V_D) \left (\dfrac{D'^2 R}{D'^2 R +R_L+DR_{on}+D'R_D} \right )
$$

$$
  \dfrac{V}{V_g} =  \dfrac{1}{D'} (1-\dfrac{D'V_D}{V_g}) \left (\dfrac{1}{1 + \dfrac{R_L+DR_{on}+D'R_D}{D'^2 R}} \right )
$$

Moreover, the converter efficiency is computed to be

$$
\begin{aligned}
\eta &= \dfrac{P_{out}}{P_{in}}= \dfrac{V (D'I)}{V_g I}=\dfrac{V}{V_g}D'= \dfrac{\left(1-\dfrac{D'V_D}{V_g} \right )}{\left ( 1+\dfrac{R_L+DR_{on}+D'R_D}{D'^2 R} \right )}
\end{aligned}
$$
The condiitons underwhich the converter may poerate with high efficiency can be characterised by answering the following question:

```{admonition} When does $\eta\rightarrow 1$?
:class: dropdown
- $V_D \ll V_g/D'$ and
- $R_L+DR_{on}+D'R_D\ll D'^2 R $
```

## A note on the accuracy of the averaged equivalent circuit in predicting losses

RMS values need to be used to correctly model average power loss in resistor.

$$
\begin{aligned}
P_{ave} &= \langle i^2(t) R \rangle \\
    &=\langle i^2(t) \rangle R \\
    &=I_{rms}^2 R \\
    &\neq I^2 R \quad (I=\langle i(t) \rangle)
\end{aligned}
$$

The models obtained above use average currents and voltages. For small ripples these values are very close. However, if the ripples are large the discrepency between these two models grow.

```{figure} fig/iRMS.svg
---
width: 500px
name: iRMS
---
Different current waveforms with $I_{rms} = \sqrt{D}I \sqrt{1+\dfrac{1}{3} \left ( \dfrac{\Delta i}{I}\right )^2}$.
```
The following table demonstrates the relationship between the consumed power using the average variables versus the real power computed using the RMS current value.

| current ripple  | Transistor RMS current  | $P_{ave}$ in $R_{on}$ |
|--------------|-----|-----------|
| $\Delta i =0$ | $I\sqrt{D}$ |       $DI^2R_{on}$ |
| $\Delta i =0.1I$      |  $1.00167 I\sqrt{D}$ |  $1.0033 DI^2R_{on}$ |
| $\Delta i =I$     |  $1.155 I\sqrt{D}$ |  $1.3333  DI^2R_{on}$ |




## Summary

The dc transformer model represents the primary functions of any dc-dc converter: transformation of dc voltage and current levels, ideally with 100\% efficiency, and control of the conversion ratio $M$ via the duty cycle $D$.

The model can be refined to account for loss elements such as inductor winding resistance and semiconductor on-resistances and forward voltage drops. The refined model predicts the voltages, currents, and efficiency of practical nonideal converters.

In general, the dc equivalent circuit for a converter can be derived from the inductor volt-second balance and capacitor charge balance equations. Equivalent circuits are constructed whose loop and node equations coincide with the volt-second and charge balance equations. In converters having a pulsating input current, an additional equation is needed to model the converter input port; this equation may be obtained by averaging the converter input current.
