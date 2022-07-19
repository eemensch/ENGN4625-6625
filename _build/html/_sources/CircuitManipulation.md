# Converter Circuit Manipulation

In this chapter we answer the following questions:
- Where do the boost, buck-boost, and other converters originate?
- How can we obtain a converter having given desired properties?
- What converters are possible?

## Circuit Manipulation

### Inversion

Let's revisit our trusty friend, the buck converter whose behaviour was derived from the first principles. We (hopefully) remember that the SPDT switch changes the dc component, and the output low-pass filter removes switching harmonics. The conversion ratio was $M(D)=D$.

```{figure} fig/buck.svg
---
width: 500px
---
Schematic of a buck converter.
```
Let's look at the circuit as a two-port network comprised of an SPDT switch and an inductor. In a buck converter, the flow of power is from the source to the load as depicted in {numref}`power_l2r`.

```{figure} fig/CircuitManip/power_l2r.svg
---
width: 500px
name: power_l2r
---
Power direction from the source to the load, $V_2= DV_1$.
```
Now, consider the case where we swap the positions of the source and the RC load. The circuit is presented in {numref}`power_r2l`. In this case the power still travels from the source to the load.

```{figure} fig/CircuitManip/power_r2l.svg
---
width: 500px
name: power_r2l
---
Power direction from the source to the load, $V_2= DV_1 \implies V_1 = \dfrac{1}{D}V_2$.
```
While we can do this for an ideal SPDT switch, the reversal of power flow requires new realisation of switches. The switches in {numref}`power_r2l` can be realised as shown in {numref}`power_r2l_semi`.

```{figure} fig/CircuitManip/power_r2l_semi.svg
---
width: 500px
name: power_r2l_semi
---
Power direction from the source to the load with semiconductor switches.
```
In this case the transistor conducts when switch is in position 2
If we interchange $D$ and $D'$ (the choice of the intervals are really arbitrary) we obtain  $V_1=\dfrac{1}{D'}V_2$.

```{attention}
Inversion of buck converter yields boost converter
```
We call this type of manipulation, ___inversion___.

### Cascade Interconnection

Next, we look into ___cascade interconnection___.

Consider the case of {numref}`cascade`, where two converters are connected back-to-back. Let's further assume that both converters are driven with the same duty cycle signal (it does not have to be the case.).


```{figure} fig/CircuitManip/cascade.svg
---
width: 500px
name: cascade
---
The cascade interconnection of two converters.
```

In this case, it is easy to note that $V_1=M_1(D)V_g$ and $V=M_2(D)V_1$. Together they imply

$$
\dfrac{V}{V_g}= M_1(D)M_2(D)
$$




````{prf:example} The cascade interconnection of a buck and a boost converter
:label: bb-cascade
:nonumber:

Here we consider the scenario where a buck converter and a boost converter are placed in a cascade interconnection as illustrated below.

```{image} fig/CircuitManip/buck_cascade_boost.svg
:width: 700px
:align: center
```
From the steady-state analysis of buck and boost converters, we have

$$
\dfrac{V_1}{V_g}=D,\quad \dfrac{V}{V_1}=\dfrac{1}{1-D}
$$

$$
\dfrac{V}{V_g}=\dfrac{D}{1-D}
$$

If we remove $C_1$ we get:

```{image} fig/CircuitManip/bb_int1.svg
:width: 500px
:align: center
```
Combining $L_1$ and $L_2$ and replacing them by $L$ results in the following noninverting buck-boost converter:
```{image} fig/CircuitManip/bb_int2.svg
:width: 500px
:align: center
```
This converter has two SPDT switches that can be driven independently with two different duty cycles. However, it is possible to arrive at a circuit realisation with only one SPDT. To this end, let's look closer to how the current in the inductor travels through the circuit. Let's consider the next circuit diagram with a dot on the inductor indicating that the current enters the inductor from that direction:
```{image} fig/CircuitManip/buck_boost_dot.svg
:width: 500px
:align: center
```
In the first interval when both switches are in position 1, the circuit looks like this:

```{image} fig/CircuitManip/bb_intv1.svg
:width: 200px
:align: center
```
In the second interval when both switches are in position 2, it will look like this:

```{image} fig/CircuitManip/bb_noninv_intv2.svg
:width: 200px
:align: center
```
Of course, these correspond to the noninverting buck-boost converter introduced earlier. But consider the thought experiment of flipping the inductor in the second interval. Then the circuit would look like this:

```{image} fig/CircuitManip/bb_intv2.svg
:width: 200px
:align: center
```
Interestingly this second interval is consistent with a case where the one side of the inductor is always connected to the ground (compare this circuit and the one corresponding to the first interval). Hence, one can realise the circuit with only one SPDT switch:  

```{image} fig/CircuitManip/bb.svg
:width: 350px
:align: center
```
````
Properties of buck-boost converter follow from its derivation as buck cascaded by boost. The equivalent circuit model follows immediately. The buck's $1:D$ transformer is cascaded by boost $D':1$ transformer. One has to consider the pulsating input current of the buck converter and the pulsating output current of boost converter in deriving the equivalent circuit.

Other cascade connections are possible. For example, \'{C}uk converter is obtained by a boost converter cascaded by a buck converter.

### Differential Interconnection

Differential connection of load between two converters can be used to obtain bipolar output voltage. An example is given in {numref}`diff`.

```{figure} fig/CircuitManip/Lecture_10-figure21.svg
---
width: 350px
name: diff
---
The differential interconnection of load between two converters.
```

Differential load voltage is

$$
V=V_1-V_2
$$
The outputs $V_1$ and $V_2$ may both be positive, but the differential output voltage $V$ can be positive or negative. While the converters can be driven using uncorrelated duty cycles, one can choose $D_1=D$ and $D_2=D'$.

Consider the case where the converters are buck converters as shown in {numref}`diff_buck`. In this case Converter 1 transistor is driven with duty cycle $D$ and Converter 2 transistor driven with duty cycle complement $D'$.
```{figure} fig/CircuitManip/Lecture_10-figure22.svg
---
width: 350px
name: diff_buck
---
The differential interconnection of load between two buck converters.
```

 The differential load voltage is

$$
\begin{aligned}
  V &=DV_g-D'V_g\\
  &= (2D-1)V_g
\end{aligned}
$$

The conversion ratio of the differentially connected buck converters is $M(D)=2D-1$ and is plotted below.

```{figure} fig/CircuitManip/diff_buck_M.svg
---
width: 350px
name: diff_buck_M
---
The differential interconnection of load between two converters.
```

We can further simplify the converter circuit. Instead of putting two output capacitors, one can bypass the load directly with one capacitor as demonstrated below:

```{image} fig/CircuitManip/Lecture_10-figure24.svg
:width: 350px
:align: center
```

In turn the inductors can be consolidated into one (remember the notion of equivalent impedance from your elementary circuit course). This results in the following circuit:
```{image} fig/CircuitManip/Lecture_10-figure25.svg
:width: 350px
:align: center
```
Equivalently, this circuit can be rearranged as the one given in {numref}`HBridge`. This is an H-bridge and is commonly used in single-phase inverter applications and in servo amplifier applications.

```{figure} fig/CircuitManip/Lecture_10-figure26.svg
---
width: 350px
name: HBridge
---
H-bridge or a bridge inverter.
```
One can connect three converters to construct a three-phase inverter and to connect to a three-phase load as shown below:

```{figure} fig/CircuitManip/3p_conv.svg
---
width: 400px
name: 3p_conv
---
Three converters connected differentially to form an inverter.
```

With balanced three-phase load, neutral voltage is:

$$
V_n = \dfrac{1}{3} (V_1+V_2+V_3)
$$

Phase voltages:

$$
V_{an}=V_1-V_n
$$

$$
V_{bn}=V_2-V_n
$$

$$
V_{cn}=V_3-V_n
$$

In practical realisations of such converters, we need to control converters such that their output voltages contain the same dc biases. This dc bias will appear at the neutral point $V_n$. It then cancels out, so phase voltages contain no dc bias.

Similar to the single phase case, one can consider a three-phase differential connection of three buck converters:
```{image} fig/CircuitManip/3p_diff_conv.svg
:width: 500px
:align: center
```
Or equivalenly:
```{image} fig/CircuitManip/3p_diff_conv2.svg
:width: 500px
:align: center
```
This is known as the _Voltage-source inverter_ or buck-derived three-phase inverter.

## A short list of converters

- Single-input single-output converters containing one inductor
  - Use switches to connect inductor between source and load,in one manner during first subinterval and in another during second subinterval
  - There are a limited number of ways to do this,so all possible combinations can be found
  - After elimination of degenerate and redundant cases,eight converters are found:
    - dc-dc converters (buck, boost, buck-boost, noninverting buck-boost)
    - dc-ac converters (bridge, Watkins-Johnson)
    - ac-dc converters (current-fed bridge, inverse of Watkins-Johnson)

### Converters producing unipolar output voltage

__Buck converter, $M(D)=D$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/buck_mini.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/buck_M.svg
:width: 400px
:align: center
````
`````

__Boost converter, $M(D)=\dfrac{1}{1-D}$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/boost_mini.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/boost_M.svg
:width: 400px
:align: center
````
`````

__Buck-boost converter, $M(D)=-\dfrac{D}{1-D}$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/bb_mini.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/BUCK_BOOST_M.svg
:width: 400px
:align: center
````
`````

__Noninverting buck-boost converter, $M(D)=\dfrac{D}{1-D}$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/noninv_bb.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/noninv_BUCK_BOOST_M.svg
:width: 400px
:align: center
````
`````

### Converters producing bipolar output voltage

__Bridge, $M(D)=2D-1$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/Lecture_10-figure26.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/diff_buck_M.svg
:width: 400px
:align: center
````
`````

__Watkins-Johnson, $M(D)=\dfrac{2D-1}{D}$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/WJ.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/watkins.svg
:width: 400px
:align: center
````
`````

__Current-fed bridge, $M(D)=\dfrac{1}{2D-1}$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/current_fed_bridge.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/current_fed.svg
:width: 400px
:align: center
````
`````

__Inverse Watkins-Johnson, $M(D)=\dfrac{D}{2D-1}$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/Inverse_WJ.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/inv_watkins.svg
:width: 400px
:align: center
````
`````
### Some Converters in the class of two-inductor converters

__&Cacute;uk, $M(D)=-\dfrac{D}{D-1}$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/cuk_mini.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/BUCK_BOOST_M.svg
:width: 400px
:align: center
````
`````

__SEPIC, $M(D)= \dfrac{D}{D-1}$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/SEPIC.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/noninv_BUCK_BOOST_M.svg
:width: 400px
:align: center
````
`````

__Inverse of SEPIC, $M(D)= \dfrac{D}{D-1}$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/Inverse_SEPIC.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/noninv_BUCK_BOOST_M.svg
:width: 400px
:align: center
````
`````

__Buck${}^2$, $M(D)= D^2$__

`````{tab-set}
````{tab-item} Circuit
```{image} fig/CircuitManip/buck2.svg
:width: 400px
:align: center
```
````

````{tab-item} Conversion Ratio
```{image} fig/CircuitManip/buck2_M.svg
:width: 400px
:align: center
````
`````

## Summary

The boost converter can be viewed as an inverse buck converter, while the buck-boost and &Cacute;uk converters arise from cascade connections of buck and boost converters. The properties of these converters are consistent with their origins. Ac outputs can be obtained by differential connection of the load. An infinite number of converters are possible, and several are listed in this chapter.
