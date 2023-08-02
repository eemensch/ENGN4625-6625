# Realising Switches Using Semi-conductor Devices

All power semiconductor devices function as SPST switches whose schematic is presented below.

```{image} fig/SPST.svg
:width: 200px
:align: center
```

Consider the buck converter depicted in {numref}`BuckSPDT`.  The converter involves a single pole double throw (SPDT) switch.

```{figure} fig/BuckSPDT.svg
---
width: 400px
name: BuckSPDT
---
Schematic of a buck converter with an SPDT switch.
```
However, in practice such a device is realised using two single-pole single throw switches as shown in {numref}`BuckSPST`.

```{figure} fig/BuckSPST.svg
---
width: 400px
name: BuckSPST
---
Schematic of a buck converter with two SPST switches.
```
Replacing a single SPDT switch with two SPST switches is a nontrivial step as two SPST switches are not exactly equivalent to one SPDT switch. It is possible for both SPST switches to be simultaneously ON or OFF. Behaviour of converter is then potentially significantly modified. For example, the discontinuous conduction mode is a consequence of using two switches to realise an SPDT switch. Conducting state of an SPST switch may depend on applied voltage or current. For example, in the case of using a diode, the voltage at the two terminals or the current going through the diode determines if it conducts or not.

SPST switches can be categorised into the following categories:

- Single-quadrant switches
- Two-quadrant switches
  - Current-bidirectional two-quadrant switch
  - Voltage-bidirectional two-quadrant switch
- Four-quadrant switch

In what follows we explore these categories.

## Single-quadrant switches

Any switch is either _active_ or _passive_. Active switches are those that the switch state is controlled exclusively by a third terminal (also known as a control terminal), e.g. transistors. Passive switches on the other hand, are those where the switch state is controlled by the applied current and/or voltage at its terminals, e.g. diode. SCR (Silicon Controlled Rectifier), are a special case &mdash turn-on transition is active, while turn-off transition is passive.
In single-quadrant switches the on-state $i$ and off-state $v$ are unipolar.

### Diode

Diodes are passive, single-quadrant switches. They conduct positive on-state currents and block negative off-state voltages. If the intended on-state and off-state operating points lie on the diode $i-v$ characteristic depicted in {numref}`diode_char`, then the switch can be realised using a diode. The voltage and current polarities are consistent with {numref}`diode_polar`

```{figure} fig/diode_char.svg
---
width: 400px
name: diode_char
---
Instantaneous $i-v$ characteristic of diodes
```

```{figure} fig/diode_polar.svg
---
width: 200px
name: diode_polar
---
Assumed voltage and current polarities in {numref}`diode_char`.
```
### Transistors

Bipolar Junction Transistor (BJT) and Insulated Gate Bipolar Transistor (IGBT) are examples for power transistors used for realising switches. They are active, single-quadrant switches, controlled by terminal $C$. Transistors conduct positive on-current and block positive off-state voltage. If the intended on-state and off-state operating points lie on the transistor $i-v$ characteristic as shown in {numref}`trans_char`, then switch can be realised using a BJT or IGBT. The voltage and current polarities are consistent with {numref}`trans_polar`.

```{figure} fig/transistor_char.svg
---
width: 400px
name: trans_char
---
Instantaneous $i-v$ characteristic of BJTs and IGBTs
```

```{figure} fig/trans_polar.svg
---
width: 400px
name: trans_polar
---
Assumed voltage and current polarities in {numref}`trans_char`.
```


````{prf:example} Switches in a buck converter
:label: buck-switch-example
:nonumber:

How can one realise the SPDT switch in a buck converter of {numref}`BuckSPDT` using transistors and diodes?

First, one needs to determine the polarities (signs) of the currents that switch A and switch B need to conduct in their on state. Then, the polarities of the voltages that the switches need to block in their off state need to be determined. For the choices of reference current direction and voltage polarity {numref}`BuckSPDT` for each of the switches we have the following characteristics:

```{image} fig/buck_switch_char.svg
:width: 400px
:align: center
```
Consulting {numref}`diode_char` and {numref}`trans_char` one concludes that switch A is consistent with a transistor and switch B can be realised with a diode.

The final converter circuit schematic with the semi-conductor devices is shown below.

```{image} fig/semi_buck_realis.svg
:width: 500px
:align: center
```

````

Metal-Oxide Semiconductor Field Effect Transistors (MOSFET) are another example of an active switch that is controlled by a terminal. These devices are normally used as single-quadrant switches, even though, they can conduct currents in both direction due to the presence of their _body diode_.
The MOSFET $i-v$ characteristic is shown in {numref}`power_transistor`. The voltage and current polarities are consistent with {numref}`MOSFET`.

```{figure} fig/power_transistor.svg
---
width: 400px
name: power_transistor
---
Instantaneous $i-v$ characteristic of power MOSFET
```

```{figure} fig/MOSFET.svg
---
width: 200px
name: MOSFET
---
Assumed voltage and current polarities in {numref}`power_transistor`.
```

In practice, to prevent the body diode from conducting (as it is a slow diode), external anti-parallel diodes are connected to a power MOSFET as shown in {numref}`MOSFETAnti`.

```{figure} fig/MOSFETAnti.svg
---
width: 200px
name: MOSFETAnti
---
External diodes to prevent conduction of body diode. The body diode is the one inside the dashed-line square.
```
If one retires the switch to conduct current in the both directions, a current-bidirectional two-quadrant switch must be used.

## Two-Quadrant Switches

### Current-bidirectional two-quadrant switch

Such switches are usually packaged as an active switch, controlled by terminal $C$ where it can conduct positive and negative on-state current and can block positive off-state voltage. If the intended on-state and off-state operating points lie on the composite $i-v$ characteristic as demonstrated in {numref}`transistor_diode_char`, then the switch can be realised using the diode/transistor composite circuit of {numref}`diode_trans`.


```{figure} fig/transistor_diode_char.svg
---
width: 400px
name: transistor_diode_char
---
Instantaneous $i-v$ characteristic of a current-bidirectional two-quadrant switch
```

```{figure} fig/diode_trans.svg
---
width: 200px
name: diode_trans
---
An example of a diode/transistor composite circuit with the assumed voltage and current polarities in {numref}`transistor_diode_char`.
```

````{prf:example} A simple inverter
:label: inverter_example
:nonumber:


Current-bidirectional two-quadrant switches can be used to construct a simple inverter. Consider the circuit depicted in {numref}`inverter`.

```{figure} fig/inverter.svg
---
width: 500px
name: inverter
---
A simple inverter realised with current-bidirectional two-quadrant switches that turns an input dc voltage to ac voltage.
```
Solving the inverter using the methods of steady-state analysis of the converters we arrive at the following relationship

$$
v_0(t)=(2D-1)V_g
$$

This relationship is depicted in {numref}`inv_MD`
```{figure} fig/sin_mod.svg
---
width: 500px
name: inv_MD
---
The output voltage of the inverter presented in {numref}`inverter` as a function of the duty cycle $D$.
```

One can modulate the duty cycle sinusoidally to produce an ac output. Let

$$
D(t) = 0.5 +D_m \sin (\omega t)
$$

Then,

$$
v_0(t)= 2 D_m V_g \sin (\omega t)
$$

The resulting inductor current variation is also sinusoidal:

$$
i_L(t)=\dfrac{v_0(t)}{R}=(2D-1) \dfrac{V_g}{R}
$$

Hence, current-bidirectional two-quadrant switches are required.
````

````{prf:example} Battery charger/discharger
:label: charger_example
:nonumber:


It is common to use a dc-dc converter with bidirectional power flow when interfacing batteries to a circuit that can act as a sink for the power as well as the source. In such cases, current-bidirectional two-quadrant switches can be used to design a battery charger/discharger as presented in {numref}`charger`.

```{figure} fig/charger.svg
---
width: 500px
name: charger
---
A converter for charging and discharging.
```
````

### Voltage-bidirectional two-quadrant switch

A voltage-bidirectional two-quadrant switch is often an active switch, and is controlled by terminal $C$ where it can conduct positive on-state current and can block positive and negative off-state voltage. If the intended on-state and off-state operating points lie on the composite $i-v$ characteristic as demonstrated in {numref}`bi_dir_voltage`, then the switch can be realised using the diode/transistor composite circuit of {numref}`series_dt`.


```{figure} fig/bi_dir_voltage.svg
---
width: 400px
name: bi_dir_voltage
---
Instantaneous $i-v$ characteristic of a voltage-bidirectional two-quadrant switch
```

```{figure} fig/series_dt.svg
---
width: 200px
name: series_dt
---
An example of a series interconnection of a diode and a transistor composite circuit with the assumed voltage and current polarities in {numref}`bi_dir_voltage`.
```

## Four-quadrant switch
 Four-quadrant switches are active switches that can conduct current in either directions and can block any polarities of voltage. Three possible realisation of such switches are presented below.

```{image} fig/Quad1.svg
 :width: 200px
 :align: center
```
```{image} fig/Quad2.svg
 :width: 200px
 :align: center
```
```{image} fig/Quad3.svg
  :width: 200px
  :align: center
```

## Synchronous rectifiers

One may want to replace the diode with a backwards-connected MOSFET, to obtain reduced conduction losses. Thus instead of using a diode with the polarity shown in {numref}`diode_polar`, one can connect a MOSFET as illustrated in {numref}`synchrect`.

```{figure} fig/synchrect.svg
---
width: 200px
name: synchrect
---
MOSFET as a synchronous rectifier.
```

```{figure} fig/reverse_mosfet_char.svg
---
width: 400px
name: synchrect_iv
---
Instantaneous $i-v$ characteristic of a MOSFET as a synchronous rectifier switch
```

When efficiency is important (almost always!) a synchronous rectifier should be used instead of a diode. A common application example is designing power supplies in low-voltage high-current applications, especially computer power supplies.

````{prf:example} Buck converter with synchronous rectifier
:label: synchronous_rectifier
:nonumber:

The schematic of a buck converter with synchronous rectifiers is given below

```{image} fig/buck_synch.svg
  :width: 700px
  :align: center
```

MOSFET $Q_2$ is controlled to turn on when diode would normally conduct. Semiconductor conduction loss can be made arbitrarily small, by reduction of MOSFET on-resistances. Thus, the losses can be made small in high-current applications. Using a synchronous rectifier transforms a discontinuous conduction mode scenario to a continuous one. (because even at no-load/ low inductor, the MOSFET can conduct in both direction.)

The drawback, is the long _reverse recovery time_ of the body diode. The main MOSFET should be off when the synchronous rectifier is off, and vice versa. Otherwise it leads to _shoot-through_. This is due to the fact that while the body-diode is recovering when the MOSFET is off it acts like a short-circuit.
A schottkey diode (fast recovery) in parallel with MOSFET's body diode will be used instead to make sure the body diode does not conduct.

````



## Summary

How an SPST ideal switch can be realised using semiconductor devices depends on the polarity of the voltage which the devices must block in the off-state, and on the polarity of the current which the devices must conduct in the on-state.
Single-quadrant SPST switches can be realised using a single transistor or a single diode, depending on the relative polarities of the off-state voltage and on-state current.
Two-quadrant SPST switches can be realised using a transistor and diode, connected in series (bidirectional-voltage) or in anti-parallel (bidirectional- current). Several four-quadrant schemes were also listed.

A _synchronous rectifier_ is a MOSFET connected to conduct reverse current, with gate drive control as necessary. This device can be used where a diode would otherwise be required. If a MOSFET with sufficiently low Ron is used, reduced conduction loss is obtained.
