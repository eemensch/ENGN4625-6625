# Discontinuous Conduction Mode (DCM)

The discontinuous conduction mode (DCM) occurs because switching ripple in inductor current or capacitor voltage causes polarity of applied switch current or voltage to reverse, such that the current- or voltage-unidirectional assumptions made in realising the switch are violated. It commonly occurs in dc-dc converters and rectifiers, having single- quadrant switches. May also occur in converters having two-quadrant switches.
Typical examples of cases where DCM occurs are dc-dc converter operating at light load (small load current). Sometimes, dc-dc converters and rectifiers are purposely designed to operate in DCM at all loads.

Properties of converters change radically in DCM:
- The conversion ratio $M$ becomes load-dependent
- Output impedance is increased
- Dynamics are altered
- Control of output voltage may be lost when load is removed

## Origins of the discontinuous conduction mode and mode boundary



We start this section by considering a buck converter with single-quadrant switches.

```{figure} fig/buck-figure0.svg
---
width: 500px
name: buck_with_diode
---
Schematic of a buck converter with single-quadrant switches.
```

Minimum diode current: $I-\Delta i_L$
DC component $I=V/R$
Current ripple:

$$
\Delta i_L = \dfrac{V_g-V}{2L}DT_s=\dfrac{V_g D D' T_s}{2L}
$$

The inductor and diode currents for the case where the converter operates _normally_ in the continuous conduction mode (CCM) are depicted in {numref}`buck_ccm_current`.
Note that $I$ depends on the load, but $\Delta i_L$ does not.

```{figure} fig/buck_ccm.svg
---
width: 400px
name: buck_ccm_current
---
Inductor and diode currents in a buck converter operating in continuous conduction mode (CCM).
```
Now consider the case where $R$ is increased until $I=\Delta i_L$. The inductor and diode currents for this case are presented in {numref}`buck_CCM_DCM_boundary`.

```{figure} fig/buck_CCM_DCM_boundary.svg
---
width: 400px
name: buck_CCM_DCM_boundary
---
Inductor and diode currents in a buck converter operating at the boundary between the continuous conduction mode (CCM) and the discontinuous conduction mode (DCM) where $I=\Delta i_L$.
```
In the next case, let's increase $R$, until $I<\Delta i_L$. We note that the load current will remain positive and nonzero.

```{figure} fig/buck_DCM.svg
---
width: 400px
name: buck_DCM
---
Inductor and diode currents in a buck converter operating in discontinuous conduction mode (CCM).
```
Now we are ready to define _Mode Boundary_ and _critical load resistance_ $R_{crit}$.

- In CCM: $I>\Delta i_L$
- DCM: $I<\Delta i_L$
Using the expressions for $I$ and $\Delta i_L$ from the steady state analysis of buck converters, the DCM condition can be stated as

$$
\dfrac{DV_g}{R}<\dfrac{DD' T_S V_g}{2L} \implies \dfrac{2L}{R T_s}<D'
$$

Define $K=\dfrac{2L}{R T_s}$ and $K_{crit}(D')=D'$. We can write the DCM condition as

 $$
 K<K_{crit}(D).
 $$
Alternatively defining Critical load resistance $R_{crit}=\dfrac{2L}{D' T_S}$, one can express the CCM and DCM conditions as the following:

 $$
 R<R_{crit}(D),\quad \text{Converter operating in CCM}
 $$

 $$
 R>R_{crit}(D),\quad \text{Converter operating in DCM}
 $$

The relationship among $K$, $K_{crit}$, and $D$ for the two cases of $K<1$ and $K>1$ in a buck converter is depicted in {numref}`K_Kcrit`.

 ```{figure} fig/K_Kcrit.svg
 ---
 width: 700px
 name: K_Kcrit
 ---
 CCM and DCM for different values of $K$, $K_{crit}$, and $D$ for a buck converter.
 ```


 Next, we shift our focus to the analysis of a boost converter ({numref}`boost_DCM`) operating in DCM.

 ```{figure} fig/boost_DCM.svg
 ---
 width: 500px
 name: boost_DCM
 ---
 Schematic of a boost converter with single-quadrant switches.
 ```
 As in the case of a buck converter:

 - In CCM: $I>\Delta i_L$
 - DCM: $I<\Delta i_L$

 Using the expressions for $I=\dfrac{V_g}{D'^2 R}$ and $\Delta i_L=\dfrac{V_g}{2L}DT_s$ from the steady-state analysis of boost converters, the converter operates in CCM when

 $$
 \dfrac{V_g}{D'^2R}>\dfrac{D T_s V_g}{2L}
 $$

 $$
 \dfrac{2L}{R T_s}>D D'^2
 $$

 Similar to the buck converter case the mode boundary can be stated as

 $$
 K>K_{crit}(D),\quad \text{Converter operating in CCM}
 $$

 $$
 K<K_{crit}(D),\quad \text{Converter operating in DCM}
 $$
where $K=\dfrac{2L}{R T_s}$ and $K_{crit}(D)=D D'^2$ as shown below.

```{image} fig/boost_boundary_mode.svg
:width: 350px
:align: center
```


CCM-DCM mode boundaries for the buck, boost, and buck-boost converters are summarised in the following tables


Converter |  $K_{crit}(D)$ | $\underset{0\leq D\leq 1}{\max} K_{crit}(D)$ | $R_{crit}(D)$ | $\underset{0\leq D \leq 1}{\min} R_{crit}(D)$|
 |:--------------:|:-----:|:-----------:|:-----:|:-----------:|
Buck |  $1-D$ | 1 | $\dfrac{2L}{(1-D)T_s}$ | $2\dfrac{L}{T_s}$|
Boost |  $D(1-D)^2$ | $\dfrac{4}{27}$ | $\dfrac{2L}{D(1-D)^2T_s}$ | $\dfrac{27}{2}\dfrac{L}{T_s}$|
Buck-boost |  $(1-D)^2$ | 1 | $\dfrac{2L}{(1-D)^2T_s}$ | $2\dfrac{L}{T_s}$

## Derivation of the conversion ratio $M(D,K)$ of a converter in DCM

In steady-state inductor volt-second balance and capacitor charge-second balance relationships are satisfied. In other words:

$$
\langle v_L \rangle =\dfrac{1}{T_s} \int_0^{T_s} v_L(t)dt=0
$$


$$
\langle i_C \rangle =\dfrac{1}{T_s} \int_0^{T_s} i_C(t)dt=0
$$

Small ripple approximation, on the other hand, sometimes applies. Specifically,     $v(t)\approx V$ is a good approximation because $\Delta v \ll V$ while    $i(t)\approx I$ is not a good approximation for the cases that $\Delta i > I$ which is the root cause of DCM.

As in CCM, converter steady-state equations obtained via charge balance on each capacitor and volt-second balance on each inductor. One has to be careful in applying small ripple approximation.

````{prf:example} Analysis of buck converter in DCM
:label: dcm-buck
:nonumber:

Here we consider the case where a buck converter is operating in DCM and how its conversion ratio, $M(D,K)$, can be derived. As the buck converter is operating in DCM, there will be an interval in which neither the diode nor the transistor is on. The buck converter and the _three_ switching intervals are illustrated below.
```{image} fig/Buck_DCM_Intervals.svg
:width: 700px
:align: center
```

In Interval 1 where the diode is off and the transistor is on, applying KVL and KCL yield

$$
v_L(t)=V_g-v(t)
$$

$$
i_C(t)=i_L(t)-v(t)/R
$$

Applying the small ripple approximation for $v(t)$ (not for $i_L(t)$) results in

$$
v_L(t)\approx V_g-V
$$

$$
i_C(t)\approx i_L(t)-V/R.
$$

Similar to above, in Interval 2 where the diode is on and the transistor is off, applying KVL and KCL lead to

$$
v_L(t)=-v(t)
$$

$$
i_C(t)=i_L(t)-v(t)/R
$$

Applying small ripple approximation for $v(t)$ (not for $i_L(t)$) one obtains

$$
v_L(t)\approx -V
$$

$$
i_C(t)\approx i_L(t)-V/R
$$

Finally, in interval 3 where both the diode  and the transistor are off, we have

$$
v_L(t)=0,\quad i_L(t)=0
$$

$$
i_C(t)=i_L(t)-v(t)/R
$$

From Small ripple approximation:

$$
v_L(t)=0
$$

$$
i_C(t)\approx -V/R
$$

The inductor voltage across these three intervals is depicted below.
```{image} fig/buck_V_dcm.svg
:width: 400px
:align: center
```
The inductor volt-second balance gives

$$
\langle v_L(t) \rangle = D_1(V_g-V) + D_2 (-V) +D_3(0)=0
$$
Consequently,

$$
V = V_g \dfrac{D_1}{D_1+D_2}
$$
where $D_2$ is unknown.

Now let's focus on the behaviour of the inductor current. The inductor is connected to the load and the output capacitor in an RLC configuration as below
```{image} fig/RLC.svg
:width: 200px
:align: center
```
From the KCL we have

$$
i_L(t)=i_C(t)+V/R
$$
The inductor current graph is given below.
```{image} fig/buck_iL_DCM.svg
:width: 400px
:align: center
```


Capacitor charge balance leads to $\langle i_C\rangle =0$.
Hence,

$$
\langle i_L \rangle = V/R
$$ (ave_cur_dcm)

In this buck converter example, the DC component of inductor current must be computed and equated to load current. To this end, let's compute the inductor peak current:

$$
i_p=i_L(D_1 T_s) = \dfrac{V_g-V}{L}D_1T_s
$$

The average current is then computed as

$$
\begin{aligned}
  \langle i_L \rangle &=\dfrac{1}{T_s}\int  i_L(t)dt\\
  &=\dfrac{1}{2} i_{p} (D_1+D_2) \\
  &=(V_g-V)\dfrac{D_1 T_s}{2 L} (D_1 + D_2 )
\end{aligned}
$$

Equating the DC component to DC load current:

$$
\dfrac{V}{R}=(V_g-V)\dfrac{D_1 T_s}{2 L} (D_1 + D_2 )
$$

Finding $V$ involves solving two equations with unknowns).
- Inductor volt-balance: $V = V_g \dfrac{D_1}{D_1+D_2}$
- Capacitor charge-balance: $\dfrac{V}{R}=(V_g-V)\dfrac{D_1 T_s}{2 L} (D_1 + D_2 )$


Solving for $V$:

$$
\dfrac{V}{V_g}= \dfrac{2}{1+\sqrt{1+4K/D_1^2}}
$$
where $K=\dfrac{2L}{R T_s}$ and $K<K_{crit}(D)$. Thus,

$$
M(K,D)=\begin{cases}
  D & K>K_{crit}(D)\\
  \dfrac{2}{1+\sqrt{1+4K/D_1^2}} & K<K_{crit}(D)
\end{cases}
$$

````


````{prf:example} Analysis of boost converter in DCM
:label: dcm-boost
:nonumber:

Here we consider the case where a bosot converter is operating in DCM and how its conversion ratio, $M(D,K)$, can be derived. As the buck converter is operating in DCM, there will be an interval in which neither the diode nor the transistor is on. The buck converter and the _three_ switching intervals are illustrated below.
```{image} fig/Boost_DCM_Intervals.svg
:width: 700px
:align: center
```

In Interval 1 where the diode is off and the transistor is on, applying KVL and KCL yield

$$
v_L(t)=V_g
$$

$$
i_C(t)=-v(t)/R
$$

Applying the small ripple approximation for $v(t)$ (not for $i_L(t)$) results in

$$
v_L(t)\approx V_g
$$

$$
i_C(t)\approx -V/R
$$

Similar to above, in Interval 2 where the diode is on and the transistor is off, applying KVL and KCL lead to

$$
v_L(t)=V_g-v(t)
$$

$$
i_C(t)=i_L(t)-v(t)/R
$$

Applying small ripple approximation for $v(t)$ (not for $i_L(t)$) one obtains

$$
v_L(t)\approx V_g-V
$$

$$
i_C(t)\approx i_L(t)-V/R
$$

In interval 3 where both the diode  and the transistor are off, we have

$$
v_L(t)=0,\quad i_L(t)=0
$$

$$
i_C(t)=-v(t)/R
$$

From Small ripple approximation:

$$
v_L(t)=0
$$

$$
i_C(t)\approx -V/R
$$

The inductor voltage across these three intervals is depicted below.
```{image} fig/boost_V_dcm.svg
:width: 400px
:align: center
```
The inductor volt-second balance gives

$$
\langle v_L(t) \rangle = D_1(V_g-V) + D_2 (-V) +D_3(0)=0
$$
Consequently,

$$
V = V_g \dfrac{D_1+D_2}{D_2}
$$
where $D_2$ is unknown.

Now let's focus on the behaviour of the diode current. The diode is connected to the load and the output capacitor in a configuration as below
```{image} fig/DRC.svg
:width: 200px
:align: center
```
From the KCL we have

$$
i_D(t)=i_C(t)+V/R
$$
The inductor current graph is given below.
```{image} fig/boost_iL_DCM.svg
:width: 400px
:align: center
```
In the second interval the diode current is the same as the inductor current. Thus, the diode current wave form would look like the graph presented next.

The inductor current graph is given below.
```{image} fig/boost_iD_DCM.svg
:width: 400px
:align: center
```


Capacitor charge balance leads to $\langle i_C\rangle =0$.
Hence,

$$
\langle i_D \rangle = V/R
$$


In this boost converter example, the DC component of diode current must be computed and equated to load current. To this end, let's compute the didoe peak current  (which is the same as the inductor peak current):

$$
i_p=i_L(D_1 T_s) = \dfrac{V_g}{L}D_1T_s
$$

The average current is then computed as

$$
\begin{aligned}
\langle i_D \rangle &=\dfrac{1}{T_s} \int i_D(t)dt\\
&=\dfrac{1}{2} i_{p} D_2\\
&=\dfrac{V_g D_1 D_2 T_s}{2 L}
\end{aligned}
$$

Equating the DC component to DC load current:

$$
\dfrac{V}{R}=\dfrac{V_g D_1 D_2 T_s}{2 L}
$$

Finding $V$ involves solving two equations with unknowns).
- Inductor volt-balance: $V = V_g \dfrac{D_1+D_2}{D_2}$
- Capacitor charge-balance: $\dfrac{V}{R}=\dfrac{V_g D_1 D_2 T_s}{2 L}$

Solving for $V$:
$V^2-VV_g-\dfrac{V_g^2 D_1^2}{K}$, $K=\dfrac{2L}{RT_s}$. Thus,

$$
V =V_g \left (\dfrac{1\pm \sqrt{1+4D_1^2/K}}{2} \right )
$$
Rejecting the negative root:

$$
\dfrac{V}{V_g} = M(D_1,K)=\dfrac{1+ \sqrt{1+4D_1^2/K}}{2}
$$
where $K<K_{crit}(D)$. (Note that the transistor duty cycle, $D$, is equal to $D_1$.)

Thus,

$$
M(K,D)=\begin{cases}
  \dfrac{1}{1-D} & K>K_{crit}(D)\\
  \dfrac{1+\sqrt{1+4D^2/K}}{2} & K<K_{crit}(D)
\end{cases}
$$
Approximation:

$$
M(D,K)\approx \dfrac{1}{2} + \dfrac{D}{\sqrt{K}}
$$

````

In the following table CCM-DCM charactersitics of three famous converters are summarised. Remember that $K=\dfrac{2L}{R T_s}$ and DCM occurs for $K<K_{crit}$}.

Converter |  $K_{crit}(D)$ | $DCM\; M(D,K)$ | $DCM\; D_2(D,K)$ | $CCM\; M(D)$
|:--------------:|:-----:|:-----------:|:-----:|:-----------:|
Buck |  $1-D$ |$\dfrac{2}{1+\sqrt{1+4K/D^2}}$  | $\dfrac{K}{D}M(D,K)$ | $D$
Boost |  $D(1-D)^2$ | $\dfrac{1+\sqrt{1+4D^2/K}}{2} $ | $\dfrac{K}{D}M(D,K)$ | $\dfrac{D}{1-D}$
Buck-boost |  $(1-D)^2$ | $-\dfrac{D}{\sqrt{K}}$ | $\sqrt{K}$ | $-\dfrac{D}{1-D}$

## Summary

The DCM conversion ratio (DCM charactersitics) of buck, boost, and buck-boost converter are presented below.

```{figure} fig/DCM_summary.svg
---
width: 500px
name: DCM_summary
---
Summary of DCM characteristics of three converters.
```

DCM buck and boost characteristics are asymptotic to $M = 1$ and to the DCM buck-boost characteristic. DCM buck-boost characteristic is linear. CCM and DCM characteristics intersect at mode boundary. Actual $M$ follows characteristic having larger magnitude. DCM boost characteristic is nearly linear.

The discontinuous conduction mode occurs in converters containing current- or voltage-unidirectional switches, when the inductor current or capacitor voltage ripple is large enough to cause the switch current or voltage to reverse polarity.

Conditions for operation in the discontinuous conduction mode can be found by determining when the inductor current or capacitor voltage ripples and DC components cause the switch on-state current or off-state voltage to reverse polarity.

The DC conversion ratio $M$ of converters operating in the discontinuous conduction mode can be found by application of the principles of inductor volt-second and capacitor charge balance.

Extra care is required when applying the small-ripple approximation. Some waveforms, such as the output voltage, should have small ripple which can be neglected. Other waveforms, such as one or more inductor currents, may have large ripple that cannot be ignored.

The characteristics of a converter changes significantly when the converter enters DCM. The output voltage becomes load- dependent, resulting in an increase in the converter output impedance.
