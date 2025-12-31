# Lec 03 - CMOS Logic

## The Switch Model

To understand CMOS logic, we first treat transistors as ideal switches with specific characteristics regarding how well they pass logic levels (Voltage).

| **Switch Behavior** | Closed (ON) when Gate = **HIGH**           | Closed (ON) when Gate = **LOW**        |
| ------------------- | ------------------------------------------ | -------------------------------------- |
| **Connection**      | Typically in **PDN** (Pull-Down Network)   | Typically in **PUN** (Pull-Up Network) |
| **Signal Strength** | Passes **Strong 0**                        | Passes **Strong 1**                    |
|                     | Passes **Weak 1**                          | Passes **Weak 0**                      |
| **Voltage Limits**  | Output rises only to ($$V_{DD} - V_{TN}$$) | Output drops only to $$|V_{TP}|$$      |

Because NMOS is bad at passing 1s and PMOS is bad at passing 0s, we use complementary pairs (CMOS). PMOS pulls up to $$V_{DD}$$ (Strong 1), and NMOS pulls down to GND (Strong 0).

## Deriving Boolean Functions

In static CMOS, the function is determined by the connection of transistors. The construction rule is to use PUN/PDN:

* **PDN (Pull-Down Network)**: Connects output to GND.
  * A OR B -> A and B in **parallel**
  * A AND B -> A and B in **series**
* **PUN (Pull-Up Network)**: Dual/The exact complement of the PDN. Connects output to $$V_{DD}$$.

To derive the CMOS logic,&#x20;

* **Look at the PDN**: Write the boolean equation based on the NMOS connections.
  * If A and B are in series: $$A \cdot B$$
  * If A and B are in parallel: $$A + B$$
* **Invert the Overall Expression**: The physical output of a CMOS gate is always inverted (NAND, NOR, NOT).
  * $$Y = \overline{\text{PDN Expression}}$$

## Transistor Sizing & Resistance

We size transistors to achieve **Equal Worst-Case** Resistance for both pull-up and pull-down paths. This ensures the rise time ($$t_{pLH}$$) and fall time ($$t_{pHL}$$) are approximately equal.

### Physics

We start from the mobility ratio. Electrons (NMOS) are faster than holes (PMOS).

* $$\mu_n \approx 2 \mu_p$$
* So, the resistivity ratio is $$\rho_p : \rho_n \approx 2 : 1$$

As the resistance formula is:

$$
R = \frac{\rho L}{A} = \frac{\rho L}{H \times W}
$$

* $$L$$ (Length) and $$H$$ (Height/Thickness) are **fixed** by the technology process.
* We control $$W$$ (Width) to adjust Resistance.

{% hint style="info" %}
This is also why sizing usually refers to adjusting the **width**.
{% endhint %}

### Sizing for Symmetry

To achieve $$R_p = R_n$$ (Equal Resistance):

* Since PMOS is 2x more resistive per unit width, we must make it 2x wider.
* Ratio: $$W_p : W_n = 2 : 1$$ and $$\sum W_p:\sum W_n=1:2$$.

### Definitions

Some other definitions that we might encounter

* **INV1X**: A standard unit inverter where $$R_p = R_n$$$$ $R_p = R_n$ $$. We treat the NMOS resistance as "1 unit $$R$$$$ $R$ $$".
* **Area Estimation**: Total Width Sum ($$\sum W$$) is an indicator of the total silicon area required.
