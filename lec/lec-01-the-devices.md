# Lec 01 - The Devices

The building blocks in digital circuit design are the silicon semiconductor devices, more specifically

1. the diodes
2. the MOS
3. bipolar transistors

## The Diode

Although diodes rarely occur directly in the schematic diagrams of present-day digital gates, they are still omnipresent. For instance, each MOS transistor implicitly contains a number of reverse-biased diodes. Diodes are used to protect the input devices of an IC against static charges. Also, a number of bipolar gates use diodes as a means to adjust voltage levels.

### Introduction

The diode to be discussed here is a **semiconductor&#x20;**_**pn**_**-junction**. The _pn_-junction diode is the simplest of the semiconductor devices. Figure 1.1a shows a cross-section of a typical _pn-_&#x6A;unction.

<figure><img src="../.gitbook/assets/pn-junction-diode.png" alt="" width="375"><figcaption><p>Figure 1.1 Abrupt pn-junction diode and its schematic symbol</p></figcaption></figure>

The _p_-type material is doped with _acceptor_ impurities (such as boron), which results in the presence of [**holes**](#user-content-fn-1)[^1] as the dominant or majority carriers. Similarly, the doping of silicon with _donor_ impurities (such as phosphorus or arsenic) creates an _n_-type material, where **electrons** are the majority carriers. Aluminum contracts provide access to the _p-_ and _n-_&#x74;erminals of the device. The circuit symbol of the diode, as used in schematic diagrams, is introduced in Figure 1.1c.

<figure><img src="../.gitbook/assets/diode-doping.png" alt="" width="375"><figcaption></figcaption></figure>

{% hint style="danger" %}
In a semiconductor, there are two types of charge carriers: **electrons** (with&#x20;charge of -1.602×10<sup>-19</sup> C) and **holes** (with charge of +1.602×10<sup>-19</sup> C)
{% endhint %}

### Semiconductors

Unlike metal and insulator, a unique property of semiconductor is that&#x20;impurities can be added (in a controlled manner) into it. This is called _Doping_.

* to make it n-type or p-type, and
* to change its conductivity (or resistivity).

### Origin of Current

In electronics, current is just the movement of charged particles (like tiny electrons). This movement happens in two main ways: **Drift** and **Diffusion**.

<figure><img src="../.gitbook/assets/drift-diffuse.png" alt="" width="563"><figcaption></figcaption></figure>

{% stepper %}
{% step %}
#### Drift Current

As explained clearly in the image. There is an external electric field to drive the movement of the electrons and holes to the final static state.
{% endstep %}

{% step %}
#### Diffusion Current

> TODO: Under deeper about the diffusion.

Diffusion happens whenever something spreads out from where it’s concentrated to where it’s not, e.g., from high concentration to low concentration. In other words, diffusion is driven by the **difference in concentrations**, or the **concentration gradient**.

**Analogy**: recall that when we drop an ink into the water, it will start diffusing until it reaches a static state. Similarly here, under the **diffusion**, there is no external force, the holes and electrons will spontaneously move to the correct region, to reach the final static state.
{% endstep %}
{% endstepper %}

Under both modes, the electrons and holes will move to the final static region. And this movement will never stop?

{% hint style="success" %}
The current in all electronic devices originates from either of the two mechanisms.
{% endhint %}

#### Origin of Current in different devices

Below is the table summarizing the carrier movement in different devices

| Devices                     | Movement Mechanism in on-state | Type of Carriers                                          |
| --------------------------- | ------------------------------ | --------------------------------------------------------- |
| Resistor                    | Drift                          | • Electrons (Metal) • Electrons and holes (Semiconductor) |
| Diode                       | Diffusion                      | • Electrons and holes                                     |
| Bipolar Junction Transistor | Diffusion                      | • Electrons and holes                                     |
| MOSFET                      | Drift                          | • Electrons (NMOS) • Holes (PMOS)                         |

### Operation

Diode (semiconductor pn-junction) is the simplest (2-terminal) and most&#x20;fundamental **nonlinear** circuit element.

* It allows a current flow through it easily in one direction (known as the forward  &#x20;direction, V > 0), but not in the opposite direction (known as the reverse direction, V < 0), except for the reverse breakdown egion. This is unlike a resistor, which is a linear element that has a linear current-voltage relation.
* Diode can be used as a switch and in a rectifier circuit to convert ac into dc. (CG1111A!)

#### Forward Bias

<figure><img src="../.gitbook/assets/diode-forward-bias.png" alt=""><figcaption></figcaption></figure>

* Under **forward-bias** (V > 0), an external voltage is applied such that the p-type terminal is at a **higher** (positive) voltage with respect to the n-type terminal.
* The forward current flows through the diode from the p-type side to the n-type side.
* The forward current remains small (around 0 practically) until the **cut-in voltage** is reached. It then increases quickly with a small increase in the voltage V thereafter.
* With a substantial forward current, the **voltage drop** across the diode lies in a narrow range. In other words, the voltage drop almost remains constant.

#### Reverse Bias

<figure><img src="../.gitbook/assets/diode-reverse-bias.png" alt=""><figcaption></figcaption></figure>

* Under **reverse-bias**, the voltage at p-type is lower than the voltage at n-type.
* The reverse current (around 0) flows through the diode from the n-type sied to the p-type side.
* For reverse bias voltage magnitude, $$∣V∣=V_R​<V_Z​$$ (V<sub>Z</sub> is the **breakdown voltage**), the reverse current is very small and can be treated practically as **zero**, meaning the diode is equivalent to an **open circuit**.

#### Breakdown Region

<figure><img src="../.gitbook/assets/diode-breakdown-region.png" alt=""><figcaption></figcaption></figure>

* Current, while operating in the breakdown region, can be limited by connecting a resistor, $$R$$, of suitable value in series with the $$pn$$ junction diode. ($$I=\frac{V_{DD}-V_Z}{R}$$)
* Operation in the breakdown region does not destroy the diode, provided the current through it is kept below a certain level (because of the resistor in this circuit), such that the power dissipation ($$V×I$$) is below what the diode can handle.

## BJT

### Introduction

<figure><img src="../.gitbook/assets/bjt-introduction.png" alt=""><figcaption></figcaption></figure>

* Bipolar junction transistor (BJT) is a **3-terminal** device made using a single crystal semiconductor (typically silicon), just like the pn-junction diode.
* BJT is made with **3 doped semiconductor regions**, namely **emitter**, **base** and **collector**, corresponding to the 3 terminals.
* The "active" region of the BJT is the region under (and including) the **emitter**.
* BJT is not a symmetrical device, in particular, impurities added to the emitter is at a much higher concentration than that added to collector.

### Modes of Operation

The Bipolar Junction Transistor (BJT) has two **pn-junctions**: the emitter-base junction and the collector-base junction. Each of these junctions can be either **forward biased** or **reverse biased**. However, we will not focus on the BJT, as it is not used in CMOS logic circuits.

## MOSFETs

The metal-oxide-semiconductor field-effect transistor (MOSFET, or MOS, for short) is certainly the workhorse of contemporary digital design. Its major asset, from a digital perspective, is that is performs very well as a **switch.**

<figure><img src="../.gitbook/assets/mos-as-switch.png" alt="" width="563"><figcaption></figcaption></figure>

Before moving on, let's make some conventions

1. For MOSFETs, S denotes **Source**, D denotes **drain**, G denotes **gate**, and B denotes the **body** or subtrate terminals.
2. For simplicity, we assume body (substrate) is shorted to source terminal.
3. **Source** and **drain** are physically **symmetrical**.
4. Majority charge carriers move **from source to drain**.
5. V<sub>GS</sub>: **Gate to source** voltage. Or the difference between gate voltage and source voltage. (Treat it as a vector in math, so V<sub>GS</sub>=-V<sub>SG</sub>)
6. V<sub>DS</sub>: **Drain to source** voltage.
7. V<sub>DD</sub>: Supply voltage.
8. V<sub>T</sub>: Threshold voltage.

### Introduction

There are two types of MOSFET: n-channel and&#x20;p-channel MOSFETs. Or to put it simply, just NMOS and PMOS.

<figure><img src="../.gitbook/assets/nmos-basic-structure.png" alt="" width="563"><figcaption></figcaption></figure>

* An **n-channel** MOSFET or NMOS is made using a **p-type** single-crystal silicon **substrate**.
* Heavily doped **n**<sup>**+**</sup>**-type** regions, created in the substrate, form the **source** and **drain** regions.
* The metal or polysilicon electrode on top of the thin oxide (dielectric) layer, between the **source** and **drain** regions, is called the **gate**.
* Note that MOSFET has a fourth terminal, which is the **substrate** or **body**.
* **Source terminal** is the **source of the carriers** that will flow through the channel to the **drain terminal**.
  * **Analogy**: In NMOS, we can think the drain termianl as something that sucks the **electrons** from the source (ground) to the drain. We will use this analogy in the later parts also.

### Physical Structure

<figure><img src="../.gitbook/assets/mosfet-physical-structure.png" alt=""><figcaption></figcaption></figure>

* Substrate (body) : Lightly doped
* Source, Drain : Heavily doped charge wells; symmetric
* Gate oxide (dielectric) : Insulator between gate and channel
* Gate : Controls the charge flow (creates the field effect)
* Gate length: the distance between the **source** and **drain** regions under the gate

{% columns %}
{% column width="50%" %}
<figure><img src="../.gitbook/assets/nmos-channel.png" alt=""><figcaption></figcaption></figure>

* n-type source/drain
* p-type body (substrate)
* **Electrons** flow from source to drain
* Current flows from drain to source

<figure><img src="../.gitbook/assets/nmos-schematic.png" alt=""><figcaption></figcaption></figure>

* Source is usually connected to ground (0V)
* V<sub>T</sub> is positive.
* When V<sub>GS</sub> $$\geq$$ V<sub>T</sub>, device is on.
* Linear region of operation: 0 < V<sub>DS</sub> < V<sub>GS</sub> - V<sub>T</sub>
* V<sub>Dsat</sub> = V<sub>GS</sub> - V<sub>T</sub>
{% endcolumn %}

{% column width="50%" %}
<figure><img src="../.gitbook/assets/pmos-channel.png" alt=""><figcaption></figcaption></figure>

* p-type source/drain
* n-type body (substrate)
* **Holes** flow from source to drain
* Current flows from source to drain

<figure><img src="../.gitbook/assets/pmos-schematic.png" alt=""><figcaption></figcaption></figure>

* Source is usually connected to V<sub>DD</sub>
* Drain is **not** usually connected to ground (0V).
* V<sub>T</sub> is negative.
* When V<sub>GS</sub> $$\leq$$ V<sub>T</sub>, device is on.
* Linear region of operation: 0 > V<sub>DS</sub> > V<sub>GS</sub> - V<sub>T</sub>
* V<sub>Dsat</sub> = V<sub>GS</sub> - V<sub>T</sub>
{% endcolumn %}
{% endcolumns %}

{% hint style="info" %}
The threshold voltage, V<sub>T</sub>, is the gate-source voltage at which channel is formed.

* The **channel** in a MOSFET is the path that allows current to flow between the source and the drain — under the gate oxide layer. It forms inside the semiconductor substrate (usually silicon) when we apply a voltage to the gate.
{% endhint %}

For the sake of simplicity, in this course, we will use NMOS as an example. And thus the following sections will be based on NMOS. The PMOS equivalent will be left as an exercise to the reader.

### Modes of Operations

#### Cut-off

We start when V<sub>GS</sub> = 0 -> no **channel** is formed for V<sub>DS</sub> $$\geq$$ 0 -> No current flow.

<figure><img src="../.gitbook/assets/nmos-cut-off.png" alt="" width="563"><figcaption></figcaption></figure>

#### In between cut-off and linear

We then increase V<sub>GS</sub> unilt V<sub>GS</sub> = V<sub>TH</sub>.

<figure><img src="../.gitbook/assets/nmos-between-cut-off-and-linear.png" alt="" width="563"><figcaption></figcaption></figure>

So what happens physically is that: At this point of time, **n-channel** is formed between source to drain. This is because as we increase V<sub>GS</sub>, it pushes away more holes and **attracts more electrons** to pile up near the surface of the subtrate under the gate. So the surface of **p-subtrate** effectively becomes **n-type** and is said to be **inverted** leading to formation of **n-channel**. The gate voltage at which this inversion happens is called **Threshold voltage, V**<sub>**TH**</sub>**.**

#### Linear

After that,

1. we continue increasing V<sub>GS</sub> until it is bigger than V<sub>TH</sub>. And then we stop increasing V<sub>GS</sub> and fix it.
2. Then we slowly increase V<sub>DS</sub> but it shouldn't exceed V<sub>GS</sub>-V<sub>TH</sub>.

So now, as V<sub>DS</sub> > 0, and there is an **n-channel** in between source and drain, as we have written above, the current will flow **from drain to source**.

And again, what happens physically is that:&#x20;

* With an NMOS, a conductive **n-type channel** is formed between the **source** and **drain**.
* When V<sub>DS</sub>​ (drain-to-source voltage) is small, the entire channel is uniformly formed — electrons can move easily.
* As V<sub>DS</sub>​ increases slightly, the **electric field** pushes more electrons, and **current I**<sub>**D**</sub>**​** increases **proportionally** (Ohm's law). This is valid only for **small values of V**<sub>**DS**</sub>.
* This is called **linear region** or **ohmic region** of a MOSFET.

{% hint style="info" %}
"Region" means a range of V<sub>GS</sub> and V<sub>DS</sub> values where the MOSFET shows a specific physical behavior and current-voltage or I-V relationship.
{% endhint %}

#### In between linear and saturation

Now, as we have already fixed the V<sub>GS</sub> and start increasing the V<sub>DS</sub>, we increase V<sub>DS</sub> until V<sub>DS</sub> = V<sub>GS</sub>-V<sub>TH</sub>.

<figure><img src="../.gitbook/assets/nmos-in-between-linear-saturation.png" alt="" width="563"><figcaption></figcaption></figure>

So, what happens physically now? The effective voltage between gate and source V<sub>GD</sub> = V<sub>G</sub> - V<sub>D</sub> = V<sub>GS</sub> - V<sub>DS</sub> (As V<sub>S</sub> = 0) = V<sub>GS</sub> - (V<sub>GS</sub> - V<sub>TH</sub>) = V<sub>TH</sub>. Then the channel at drain end begins to **pinch off**.

{% hint style="success" %}
Using the sucking analogy on the drain side, we can think of it as when we increase V<sub>DS</sub>, the drain will suck the electrons **more quickly**, thus the channel near to the drain will become **thinner**.
{% endhint %}

#### Saturation

As we continue increasing V<sub>DS</sub> until V<sub>DS</sub> > V<sub>GS</sub>-V<sub>TH</sub>. Let's denote three variables here:

1. $$L$$ is the channel length
2. $$\Delta L$$ is pinched-off channel length
3. $$L_{\text{eff}}$$ is the effective channel length = $$L-\Delta L$$

<figure><img src="../.gitbook/assets/nmos-saturation.png" alt="" width="563"><figcaption></figcaption></figure>

So, what happens physically? Although the channel at the drain end pinches off, the electrons still flow to drain under the influence of **high electric field in the pinch-off region** from drain to source and hence the **current is constant**.

{% hint style="warning" %}
Here, in the **pinched-off** region near the drain, there is still **n-channel**, it's just that it is very **thin**, it doesn't mean that there is no **n-channel**.
{% endhint %}

<details>

<summary>What are the short channel effects?</summary>

Basically, when transistors get **very tiny**, the gate **loses some control** over the channel, and new unwanted effects appear — those are called **short-channel effects (SCEs).**

</details>

***

In summary, we have the following table

| Condition / VDS Range                                    | Region                                     | Channel Description                                                                 | Current Behavior / Equation                                           |
| -------------------------------------------------------- | ------------------------------------------ | ----------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
|  $$V_{GS} < V_{TH}$$                                     | **Cutoff (OFF)**                           | No inversion channel formed; MOSFET is OFF                                          |  $$I_D \approx 0$$                                                    |
| $$V_{GS} \approx V_{TH}$$                                | **Boundary between Cutoff and Linear**     | Channel **just starts to form** (weak inversion); small leakage current begins      | $$I_D$$ rises exponentially with $$V_{GS}$$ (subthreshold conduction) |
| $$V_{GS} > V_{TH}$$ and $$0 < V_{DS} < V_{GS} - V_{TH}$$ | **Linear (Ohmic)**                         | Channel fully formed and uniform; acts like voltage-controlled resistor             | $$I_D =f(V_{DS}, V_{GS})$$                                            |
| $$V_{DS} = V_{GS} - V_{TH}$$                             | **Boundary between Linear and Saturation** | Channel begins to pinch off at the drain end                                        | Marks start of current saturation                                     |
| $$V_{DS} > V_{GS} - V_{TH}$$                             | **Saturation (Active)**                    | Channel pinched off near drain; current nearly constant (independent of $$V_{DS}$$) | $$I_D =f(V_{GS})$$                                                    |

### I-V characteristics

#### Output characteristic

{% stepper %}
{% step %}
#### Linear Region

In the linear region, we have two situations

* Increase in V<sub>DS</sub> leads to increase in current like **voltage-controlled resistor**.
* Increase in V<sub>GS</sub> leads to a greater number of electrons leading to higher current.

That's why $$I_D =f(V_{DS}, V_{GS})$$, and the function $$f$$ is

$$
i_D = \mu_n C_{ox} \frac{W}{L} \left[ (V_{GS} - V_T)V_{DS} - \frac{1}{2}V_{DS}^2 \right] \\
$$

where

$$
\begin{align*}
\mu_n      & \quad \text{is the electron mobility in the channel} \\
C_{ox}    & \quad \text{is the Gate oxide capacitance per unit area} \\
W         & \quad \text{is the Channel Width} \\
L         & \quad \text{is the Channel length}
\end{align*}
$$

Based on this equation, we see that $$I_D$$ doesn't increase **perfectly** linearly with $$V_{DS}$$. Only when $$V_{DS}$$ is very small -> $$\frac{1}{2}V_{DS}^2$$ is very negligible -> we can say the increasing is **linear**.

{% hint style="info" %}
The linear region is where the digital integrated design comes in.
{% endhint %}
{% endstep %}

{% step %}
#### Saturation Region

In the saturation region, only the increase in V<sub>GS</sub> will affect the current. We denote V<sub>Dsat</sub> = (V<sub>GS</sub> - V<sub>T</sub>).

<figure><img src="../.gitbook/assets/iv-characteristics-saturation-region.png" alt="" width="375"><figcaption></figcaption></figure>

That's why we have $$I_D =f(V_{GS})$$, and the function $$f$$ is

$$
i_D = i_{Dsat} = \frac{1}{2}\mu_n C_{ox} \frac{W}{L} (V_{GS} - V_T)^2
$$

where,

$$
\begin{align*}
\mu_n      & \quad \text{is the electron mobility in the channel} \\
C_{ox}    & \quad \text{is the Gate oxide capacitance per unit area} \\
W         & \quad \text{is the Channel Width} \\
L         & \quad \text{is the Channel length}
\end{align*}
$$

{% hint style="info" %}
The saturation region is where the analog integrated design comes in.
{% endhint %}
{% endstep %}
{% endstepper %}

In summary, below is the NMOS and PMOS I-V characteristics (i<sub>D</sub> and V<sub>DS</sub>), where the red cicrled part is the **linear region** and the green circled part is the **saturation region**. This is called **output characteristics**, where I<sub>D</sub> versus V<sub>DS</sub> with V<sub>GS</sub> as a parameter.

<figure><img src="../.gitbook/assets/nmos-pmos-iv-characteristics.png" alt=""><figcaption></figcaption></figure>

#### Transfer characteristic

If we draw the I-V characteristics between the V<sub>GS</sub> and i<sub>D</sub>, we will find that after V<sub>GS</sub> exceeds beyond V<sub>TH</sub>, i<sub>D</sub> will increase **quadratically** as V<sub>GS</sub> increases. This is called **transferred characteristics**, where i<sub>D</sub> versus V<sub>GS</sub> at a given fixed V<sub>DS</sub> value (V<sub>DS</sub> is chosen so that the MOSFET is in **saturation region**).

<figure><img src="../.gitbook/assets/transfer-characteristics-of-mosfets.png" alt=""><figcaption></figcaption></figure>

So, to understand its geometric meaning, we can see from the following graph,

<figure><img src="../.gitbook/assets/meaning-transfer-characteristic.png" alt=""><figcaption></figcaption></figure>

### New Transistor Architecture

As for now, we only have one gate to control the channel. Nowadays, the new transistor architecture is called 3D FET.

<figure><img src="../.gitbook/assets/3d-fet.png" alt=""><figcaption></figcaption></figure>

For example, the following is the diagram showing the **height**, **width** and **length** of FinFET and Gate-All-Around.

<figure><img src="../.gitbook/assets/finfet.png" alt="" width="420"><figcaption><p>FinFet length, width and height</p></figcaption></figure>

[^1]: "holes" refers to electron holes, which are quasiparticles representing the absence of an electron in a material like a semiconductor. These holes act as **positive charge** carriers and are crucial for modern electronics, such as diodes and transistors.
