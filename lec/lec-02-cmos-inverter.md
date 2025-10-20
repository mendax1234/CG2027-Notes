# Lec 02 - CMOS Inverter

## Inverter

An inverter can be thought of as a NOT gate. It will negate whatever value from its input.

### Ideal Inverter

An ideal inverter has the following V<sub>in</sub>-V<sub>out</sub> graph

<figure><img src="../.gitbook/assets/ideal-inverter-vin-vout.png" alt="" width="375"><figcaption></figcaption></figure>

From this graph, we can see that

1. When 0 <i class="fa-less-than-equal">:less-than-equal:</i> V<sub>in</sub> <i class="fa-less-than-equal">:less-than-equal:</i> V<sub>DD</sub> /2, V<sub>out</sub> = V<sub>DD</sub>, this means \[0, V<sub>DD</sub>/2] is Vin's **input low** range. Similarly, \[V<sub>DD</sub>/2, V<sub>DD</sub>] is Vin's **input high** range.
   1. [NM<sub>H</sub>](#user-content-fn-1)[^1]: V<sub>DD</sub> /2
   2. [NM<sub>L</sub>](#user-content-fn-2)[^2]: V<sub>DD</sub> /2
   3. [Switch threshold](#user-content-fn-3)[^3]: V<sub>DD</sub> /2
2. The meaning of **gain** is just the change rate of V<sub>out</sub> with respect to V<sub>in</sub>, which is $$d\frac{V_{out}}{V_{in}}$$

### Real Inverter

In the real world, the inverter cannot be that perfect. Its V<sub>in</sub>-V<sub>out</sub> graph is usually shown as follows

<figure><img src="../.gitbook/assets/real-inverter-vin-vout.png" alt="" width="375"><figcaption></figcaption></figure>

From this graph, we will see some very important conventions used in Electrical Engineering

1. In the V<sub>in</sub>-V<sub>out</sub> graph, we always treat x-axis as V<sub>in</sub> and y-axis as V<sub>out</sub>.
2. V<sub>OH</sub>: This is the **nominal (expected) output voltage** when the inverte**r output is logic HIGH**. This is usually around V<sub>DD</sub>.
3. V<sub>OL</sub>: This is the **nominal (expected) output voltage** when the inverter **output is logic LOW**. This is around 0V.
   1. V<sub>OH</sub> and V<sub>OL</sub> are **nominal values**, and they are **different from** the actual output, which we usually define to be just V<sub>out</sub>.
   2. Usually, V<sub>OH</sub>, V<sub>OL</sub>, together with V<sub>IL</sub> and V<sub>IH</sub> **are specified by the manufacturer** in the **logic family’s datasheet.**
4. V<sub>M</sub>: This is the **switching threshold**, where V<sub>in</sub> = V<sub>out</sub>.

#### Mapping between Analog and Digital Signals

As analog signals are **continuous** while digital signals are **discrete**, when we convert analog signals to digital signals, we need to define some "mappings". In this lecture, the following mapping is defined,

<figure><img src="../.gitbook/assets/real-inverter-vin-vout-vil-vih.png" alt="" width="375"><figcaption></figcaption></figure>

From this graph, we add on to the important conventions that will be used in Electrical Engineering

1. V<sub>IL</sub>: The **highest input voltage** that the gate will still recognize as a logic LOW.
   1. Thus, in this graph, the **input low** range is \[V<sub>OL</sub>, V<sub>IL</sub>]
2. V<sub>IH</sub>: The **lowest input voltage** that the gate will recognize as a logic HIGH.
   1. Thus, in this graph, the **input high** range is \[V<sub>IH</sub>, V<sub>OH</sub>]

#### Noise Margin

**Noise margin** is how much noise a signal can tolerate and still be **read** correctly as 0 or 1. So, in our notation, we can easily treat NM<sub>H</sub> as the length of **input high** range and NM<sub>L</sub> as the length of the **input low** range.

* NM<sub>H</sub> = V<sub>OH</sub> - V<sub>IH</sub>
* NM<sub>L</sub> = V<sub>IL</sub> - V<sub>OL</sub>

<figure><img src="../.gitbook/assets/nmh-nml.png" alt="" width="375"><figcaption></figcaption></figure>

Prof. Annie also introduces the following analogy for NM<sub>H</sub> and NM<sub>L</sub>:

* NM<sub>H</sub> defines how much the V<sub>out</sub> can **drop** from the **nominal high voltage** (V<sub>OH</sub>) for it to be **read** correctly as logic HIGH by the following gate.&#x20;
* NML defines how much the V<sub>out</sub> can **go up** from the **nominal low voltage** (V<sub>OL</sub>) for it to be **read** correctly as logic LOW by the following gate.&#x20;

#### Fan-in and Fan-out

<figure><img src="../.gitbook/assets/fan-in-fan-out.png" alt="" width="563"><figcaption></figcaption></figure>

From the above image, we can clearly see that

1. **Fan-in** means how many **inputs** a gate has, it describes the number of signals feeding **into** one logic gate
2. **Fan-out** means How many **inputs** are driven by one output the number of gates that one output signal can **drive**.

[^1]: For V<sub>out</sub> to be **high**, the acceptable range of V<sub>in</sub>

[^2]: For V<sub>out</sub> to be **low**, the acceptable range of V<sub>in</sub>

[^3]: The value of V<sub>in</sub> that causes V<sub>out</sub> to change from low to high or high to low.
