# Lec 05 - Memory

## DRAM

The basic cell used in DRAM is shown as follows:

<figure><img src="../.gitbook/assets/dram-cell.png" alt="" width="563"><figcaption></figcaption></figure>

This structure is known as **1T1C** (One transistor one capacitor). At the end of BL, we have a **sense amplifier** (We will talk about its usage later)

### Refresh

As we all know, DRAM uses capacitor to store bit information,

1. when the capacitor is charged, 1 is stored, its voltage is VDD.
2. when it is discharged, 0 is stored and its voltage is 0.

As the transistor controlled by WL cannot isolate the capacitor completely, thus having some leakage current, so the charges stored in the capacitor will slowly get away. That's why we need to recharge/refresh the capacitor peirodetically

#### Steps to Refresh

1. Preload all the Bit Lines to Vdd/2
2. Activate one word line (only one at a time) -> NMOS is ON
3. The sense amplifier at the end of each BL can detect the voltage change at the Bit Line
   1. If 1 is previously stored, the charge will move from the capacitor to the Bit Line, causing the Bit Line voltage to increase.
   2. If 0 is previously stored, the charge will move from the Bit Line to the capacitor, causing the Bit Line voltage to drop
4. Each sense amplifier will sense the voltage change at each bit line
   1. If voltage is increased, pull up bit line to constant VDD, thus 1 will be refreshed.
   2. If voltage is decreased, pull down bit line to 0, thus 0 will be refreshed.

### Read

After one refresh, the Bit Line voltage is the same as the capacitor voltage (0 or Vdd), thus we just need to read the bit line voltage to know the info (0 or 1) that is stored in the capacitor

### Write

To write a DRAM cell

1. Refresh the capcitor in the activated word line first
2. Charge the bit line voltage to the information you want to write (Vdd or 0)

<details>

<summary>Why refresh is needed?</summary>

Because not every time we are writing all the bit cells in the word line. We write some of them, but as the rest are activated. If not refreshed, the information stored will be lost.

</details>

## NAND Flash

The building block of NAND Flash is the floating gate and floating gate transistor. It will be good for us to know their working principles before we start looking at the NAND Flash

{% stepper %}
{% step %}
#### Floating Gate

Giving an electric field, strong enough. The quantum tunneling effect happens, electrons pass through the insulator to be stored in the conductor.

After that, if another strong electric field is given in the opposite direction, the electrons will be pushed out.
{% endstep %}

{% step %}
#### Floating Gate Transistor

Put the floating gate under the gate of the NMOS transistor, we can get the floating gate transistor

<figure><img src="../.gitbook/assets/floating-gate.png" alt="" width="563"><figcaption></figcaption></figure>

We can perform the following three operations on the floating gate transistor:

1. **Write/Program**: Give the gate a very high voltage, subtrate 0V, then electrons will be pulled into the floating gate and stored in it. This is called write/program.
2. **Erase**: Oppositely, we give substrate a very high voltage (e.g., 20V) and give the control gate 0V, creating an opposite electric field as we write, then electrons will be pushed out of the floating gate.
3. **Read**: Remember that the threshold voltage of the NMOS? We will use it to try -> Apply this threshold voltage at gate, substrate 0V.
   1. If there are electrons in the floating gate, they will cancel off some of the gate voltage, making the real voltage below the floating gate smaller than the threshold voltage of NMOS, thus no channel can be formed, the device is in cut-off mode.
      1. No conductions -> electrons in floating gate -> read 0.
   2. If there are no electrons in the floating gate, nothing will get cancelled off, thus the NMOS will be turned on!
      1. Got conductions -> no electron in floating gate -> read 1.
{% endstep %}

{% step %}
#### SLC/MLC/TLC/QLC

In the above section, we see that the floating gate has only **2 options**

* Have electrons
* Don't have electrons

This is called **SLC**. For the rest 3 types

1. **MLC**: 1 floating gate can store 4 states (using 2 bits)
2. **TLC:** 8 states (using 3 bits)
3. **QLC**: 16 states (using 4 bits)
{% endstep %}
{% endstepper %}

The circuit diagram for the NAND-Flash can be shown as follows:

<figure><img src="../.gitbook/assets/nand-flash.png" alt="" width="222"><figcaption></figcaption></figure>

The diagram above is called a **block** and it is composed of several **strings,** each string is controlled by one bit line. At the SSL and GSL, there are NMOS transistors, the rest controlled by different WLs are floating gate transistors. All the floating gate connected by the same word line is called a **page**.

{% hint style="info" %}
Within the same block, all the floating gate and the NMOS share the same common p-substrate.
{% endhint %}

### Read

In NAND Flash, one time read can only read one page.

1. Apply high voltage to SSL and CSL to make the NMOS conducted.
2. Apply a special high voltage to the other word lines (instead of the word line / page you are going to read). All the transistors conduct now!
   1. Special high voltage means that no matter the floating gate is full of electrons, applying this voltage can still make the transistor conduct and the voltage is not enough to trigger the tunneling effect causing the number of electrons in the floating gate to increase.
3. Apply the NMOS threshold voltage to the word line we are reading.
   1. If the floating gate got electrons, that transistor cannot conduct
   2. Otherwise, that transistor can conduct.
4. We can check the voltage at the bit line to read.

### Write

One time write can only write one page also.

1. Apply high voltage to SSL -> conducting. 0V to CSL -> cut off
2. Set all bit lines to 0V.
3. Apply the special high voltage to the other word lines (same as above)
4. Apply the very high voltage (for tunneling effect to happen) at that specific word line we are writing to
   1. If we want to write/program the floating gate, we need to suck electrons -> just let bit line to be 0V.
      1. Suck electrons -> Write 0
   2. If we don't want to write a floating gate, no suck electrons -> let bit line to be a high voltage so that the voltage difference between gate (WL) and source (high voltage) is not enough to trigger the tunneling effect, no electrons will be sucked into the floating gate.
      1. No suck electrons -> Write 1

### Erase

To erase the data stored in the NAND flash. We apply a high voltage at the subtrate. As the substrate is common, all the data on the block will be erased!
