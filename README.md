# High-Speed Hybrid-Logic Full Adder Implementation

## 📌 Project Overview
This repository contains the **Cadence Virtuoso** implementation of a high-performance Hybrid Full Adder (FA) based on a novel **10-Transistor (10-T) XOR-XNOR cell**. The project focuses on optimizing Power-Delay Product (PDP) and driving capability in VLSI arithmetic circuits.

The designs implemented here efficiently combine Pass Transistor Logic (PTL), Transmission Gates (TG), and static CMOS logic to achieve full-swing outputs with reduced transistor counts compared to conventional CMOS Full Adders.

**Key Reference:**
> J. Kandpal, A. Tomar, M. Agarwal and K. K. Sharma, "High-Speed Hybrid-Logic Full Adder Using High-Performance 10-T XOR-XNOR Cell," in *IEEE Transactions on Very Large Scale Integration (VLSI) Systems*, vol. 28, no. 6, pp. 1413-1422, June 2020.

---

## 📂 Repository Structure

The project is organized into modular cells representing the core building blocks and the complete Full Adder variations.

### 🔹 Core Modules
| Cell Name | Description |
| :--- | :--- |
| **`10T_XOR_XNOR`** | The proposed 10-transistor XOR-XNOR module. Generates simultaneous full-swing XOR and XNOR signals. |
| **`sum_a` / `sum_b` / ...** | Variations of the SUM logic module (Module II) as described in the paper. |
| **`cout_a` / `cout_b` / ...** | Variations of the CARRY logic module (Module III). |

### 🔹 Full Adder Designs
| Design | Architecture Description | Performance Characteristic |
| :--- | :--- | :--- |
| **`FA_1`** | Hybrid FA using TG-based Sum/Carry modules. | High robustness, 20 Transistors. |
| **`FA_2`** | Design-1 with output buffers. | Improved driving capability for cascaded chains. |
| **`FA_3`** | Design using input inverters/buffers. | Optimized for specific load conditions. |
| **`FA_4`** | **Proposed Best Design**. Uses CMOS-style Sum/Carry. | **Lowest PDP** and best driving strength (20T). |

---

## 🛠 Tools & Technology Used
* **EDA Tool:** Cadence Virtuoso Studio (Schematic XL, Layout XL, ADE Explorer/Assembler)
* **Simulator:** Spectre
* **Technology Node:** 90nm CMOS (GPDK090)
* **Analysis:** Transient Analysis, DC Operating Point, Power (Average), Delay (Propagation).

---

## 📊 Simulation Results
The designs have been verified for functionality and robustness. Key performance metrics evaluated include:

1.  **Propagation Delay:** Measured from $C_{in}$ to $C_{out}$ (critical path).
2.  **Power Consumption:** Average dynamic and static power at **1.8V**.
3.  **Power-Delay Product (PDP):** $PDP = Power \times Delay$.
4.  **Process Corner Analysis:** Verified across **NN (Typical)**, **SS (Slow)**, and **FF (Fast)** corners to ensure manufacturing robustness.

> **Key Finding:** `FA_4` demonstrates the best overall performance with the lowest PDP and superior signal integrity, matching the conclusions of the reference paper.

---

## 🚀 How to Use
1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/hrushi199/high-speed-hybrid-logic-full-adder.git](https://github.com/hrushi199/high-speed-hybrid-logic-full-adder.git)
    ```
2.  **Import to Cadence:**
    * Launch Cadence Virtuoso.
    * Add the library path to your `cds.lib`.
    * Use the Library Manager to browse `10T_XOR_XNOR` and `FA_*` cells.
3.  **Run Simulations:**
    * Open the `maestro` view inside any FA cell (e.g., `FA_4/maestro`).
    * Ensure the model libraries point to your local GPDK090 path.
    * Run the pre-configured test states to view waveforms and measurements.

---

## 📜 License
This project is intended for educational and research purposes. Please cite the original authors when referencing the architecture.
