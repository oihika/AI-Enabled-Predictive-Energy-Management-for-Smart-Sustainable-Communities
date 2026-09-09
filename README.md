# 🌊☀️💨🔋 Hydro-pv-wind-bess-energy-management-system

Python-based simulation of a **hybrid Hydro–PV–Wind–Battery Energy Management System (EMS)** with SCADA-inspired monitoring, renewable dispatch analysis, **Duck Curve analysis**, grid-stability indicators, and carbon-footprint evaluation.

# ⚡ Jabalpur Hydro–Solar–Wind–Battery Hybrid Energy Simulation as a Digital Prototype

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green.svg)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-purple.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange.svg)
![Renewable Energy](https://img.shields.io/badge/Domain-Renewable%20Energy-red.svg)
![Energy Storage](https://img.shields.io/badge/Storage-BESS-yellow.svg)
![Grid Stability](https://img.shields.io/badge/Grid-Stability-blueviolet.svg)
![Status](https://img.shields.io/badge/Status-Research%20Prototype-brightgreen.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## 🌞💨🌊🔋 Project Overview

This project presents a **Python-based digital simulation of a hybrid renewable energy system for Jabalpur, India**, integrating:

* ☀️ **Solar Photovoltaic (PV) Generation**
* 💨 **Wind Energy Generation**
* 🌊 **Hydropower as a Dispatchable Renewable Resource**
* 🔋 **Battery Energy Storage System (BESS)**
* 🔌 **Conventional/Fossil Grid Fallback**
* 📊 **Renewable Energy Dispatch Analysis**
* 🦆 **Duck Curve and Net-Load Analysis**
* ⚡ **Grid Stability Indicators**
* 🌍 **Carbon-Footprint Evaluation**

The Energy Management System coordinates multiple renewable resources and battery storage to meet hourly electricity demand while reducing dependence on conventional grid support.

---

## 🏗️ System Architecture

```text
                    ☀️ SOLAR PV
                        │
                        │
                        ▼
                    ┌─────────┐
                    │         │
💨 WIND ───────────►│   EMS   │◄────────── 🌊 HYDRO
                    │         │
                    └────┬────┘
                         │
              Renewable Dispatch
                         │
             ┌───────────┼───────────┐
             ▼           ▼           ▼
          🔋 BESS     🏠 LOAD     ⚡ GRID
       Charge/Discharge Demand    Support
             │                       │
             └───────────┬───────────┘
                         ▼
                  📊 SYSTEM MONITORING
                         │
            ┌────────────┼────────────┐
            ▼            ▼            ▼
       ⚡ Frequency   🔌 Voltage   🛡️ Reserve
          Stability     Stability     Margin
```

---

# 🧠 Energy Management Methodology

The simulation follows a **rule-based renewable dispatch strategy**.

### ⚡ Dispatch Priority

```text
1️⃣ Solar PV + Wind Generation
             ↓
2️⃣ Supply Load Demand
             ↓
3️⃣ Excess Renewable Energy
             ↓
4️⃣ Charge BESS
             ↓
5️⃣ Demand Deficit
             ↓
6️⃣ BESS Discharge
             ↓
7️⃣ Hydropower Dispatch
             ↓
8️⃣ Conventional/Fossil Grid Fallback
```

The model therefore uses renewable resources first and conventional generation only when the available renewable generation, storage, and hydro resources are insufficient.

---

## ☀️ Solar PV Integration

Solar PV represents the primary daytime variable renewable resource.

The model evaluates:

* Solar availability
* Solar generation
* Direct solar-to-load supply
* Midday renewable surplus
* Solar contribution to renewable penetration
* Solar-driven net-load reduction

Solar generation is particularly important for the **Duck Curve analysis**, because high daytime PV output can significantly reduce the grid's net load.

---

# 💨 Wind Energy Integration

Wind generation has been integrated as a complementary variable renewable resource.

The wind model uses an illustrative **40 MW installed wind capacity** and a simplified wind-turbine power curve.

### 🌬️ Wind Power Curve

```text
Wind Speed
    │
    ├── < 3 m/s ─────────────► 0 MW
    │
    ├── 3–12 m/s ────────────► Variable Generation
    │
    ├── 12 m/s ──────────────► Rated Power
    │
    └── ≥ 25 m/s ────────────► 0 MW
```

The simulation evaluates:

* 🌬️ Hourly wind speed
* ⚡ Available wind power
* 🔌 Dispatched wind power
* 📈 Wind capacity factor
* 🔄 Wind variability
* 🌱 Wind contribution to renewable supply
* 🦆 Wind contribution to Duck Curve mitigation

### Why Wind Matters

Wind generation can complement solar generation because its production profile does not necessarily follow the same daytime pattern as solar PV.

```text
☀️ Solar
High → Daytime
Low  → Night

💨 Wind
Variable → Throughout the day

        ↓

☀️ + 💨

Complementary Renewable Generation

        ↓

Reduced dependence on
🔌 Conventional Grid Support
```

---

# 🌊 Hydropower Integration

Hydropower is modelled as a **dispatchable renewable balancing resource**.

The hydropower model is inspired by reference operating values associated with the **Rani Avanti Bai Hydel Power Station** in the Jabalpur region.

## ⚡ Hydropower Reference Values

| Parameter            |     Value |
| -------------------- | --------: |
| ⚡ Active Power       |  34.10 MW |
| 🔌 Generator Voltage |     11 kV |
| 📡 Frequency         |     50 Hz |
| 🌊 Reservoir Level   |  409.55 m |
| 📐 Effective Head    |   39.85 m |
| 💧 Water Discharge   | 97.5 m³/s |
| 🚪 Gate Opening      |    56.25% |
| 🔄 Generator Speed   | 166.6 rpm |

Hydropower is used as a flexible renewable resource when solar, wind and battery resources cannot completely satisfy demand.

---

# 🔋 Battery Energy Storage System — BESS

The BESS provides short-term energy shifting and balancing capability.

### Charging

During periods of renewable surplus:

```text
☀️ Solar + 💨 Wind
        │
        ▼
 Renewable Surplus
        │
        ▼
      🔋 BESS
      Charging
```

### Discharging

During demand-deficit periods:

```text
🏠 High Demand
      │
      ▼
 Renewable Deficit
      │
      ▼
   🔋 BESS
  Discharge
      │
      ▼
 Reduced Grid Support
```

The model tracks:

* 🔋 Battery power
* 🔋 Battery energy
* 📊 State of Charge (SOC)
* ⚡ Charging power
* ⚡ Discharging power
* 🔄 Energy shifting
* 🌙 Evening support

---

# 🦆 Duck Curve Analysis

A major addition to this prototype is the explicit analysis of the **Duck Curve**.

The fundamental relationship is:

```text
                 Net Load
                    =
          Gross Electricity Demand
                    −
              Solar Generation
```

### ☀️ Midday Effect

High solar generation can create a significant reduction in grid net load.

```text
Gross Demand
     │
     │       ╲
     │        ╲
     │         ╲
     │          ╲
     │           ╲
     │            ╲
     │             ╲
     └──────────────────────► Time

        ☀️ Solar Generation
              ↓
       Net-load valley
```

This creates the characteristic **Duck Curve** shape.

---

## 🌅 Evening Ramp Problem

As solar generation rapidly decreases while electricity demand remains high:

```text
☀️ Solar Output
      ↓↓↓
      ↓
      ↓
      └────────► Low

🏠 Electricity Demand
      ↑
      ↑↑
      ↑↑↑

          ↓

⚠️ Rapid Net-Load Ramp
```

This evening ramp can increase the need for flexible generation and grid balancing.

---

# 🦆 Duck Curve Mitigation Strategy

The prototype evaluates how multiple resources can reduce Duck Curve stress.

```text
             MIDDAY
               │
               ▼
        ☀️ High Solar PV
               │
               ▼
        Net-Load Depression
               │
               ▼
        🔋 BESS Charging
               │
               │
               ▼
            EVENING
               │
               ▼
       ☀️ Solar Declines
               │
               ▼
        Net-Load Ramp
               │
       ┌───────┼────────┐
       ▼       ▼        ▼
     💨 Wind  🌊 Hydro  🔋 BESS
       │       │        │
       └───────┼────────┘
               ▼
       Reduced Ramp Stress
               │
               ▼
       Improved Grid Flexibility
```

The simulation calculates:

* 🦆 Duck Curve depth
* 📈 Evening net-load ramp
* 💨 Wind contribution
* 🌊 Hydro contribution
* 🔋 BESS contribution
* ⚡ Peak evening ramp
* 📉 Ramp reduction
* 📊 Duck Curve mitigation percentage

---

# ⚡ Grid Stability Monitoring

The EMS includes a simplified **Grid Stability Window** to monitor system operating conditions.

### Monitored indicators

| Indicator          | Purpose                                  |
| ------------------ | ---------------------------------------- |
| ⚡ Frequency        | Measures deviation from nominal 50 Hz    |
| 🔌 Voltage         | Monitors voltage deviation in per-unit   |
| 🛡️ Reserve Margin | Indicates available balancing capability |
| 📈 Renewable Ramp  | Measures rapid renewable-output changes  |
| 🔋 BESS SOC        | Determines available storage flexibility |
| 🌊 Hydro Dispatch  | Measures dispatchable renewable support  |

### Stability Window

The model evaluates a rolling **3-hour stability window**.

```text
Hour ───────►

⚡ Frequency
───────────────
49.5 ───────── Stable Lower Limit
50.0 ───────── Nominal
50.5 ───────── Stable Upper Limit

🔌 Voltage
───────────────
0.95 ───────── Stable Lower Limit
1.00 ───────── Nominal
1.05 ───────── Stable Upper Limit

🛡️ Reserve
───────────────
≥ 10% ─────── Preferred minimum
```

The system classifies operating conditions as:

* 🟢 `STABLE`
* 🟡 `WARNING`
* 🔴 `STRESS`

and the rolling window as:

* `INITIALIZING`
* `STABLE WINDOW`
* `WATCH`
* `UNSTABLE WINDOW`

---

# 📊 Outputs & Visualizations

The simulation generates multiple analytical visualizations.

### ⚡ 1. Four-Source Renewable Dispatch

Shows:

* ☀️ Solar
* 💨 Wind
* 🌊 Hydro
* 🔋 BESS
* 🏠 Demand

### 💨 2. Wind Resource and Dispatch

Shows:

* Wind speed
* Available wind power
* Dispatched wind power

### 🔋 3. Battery State of Charge

Shows hourly BESS SOC and operating limits.

### 📈 4. Demand–Supply Balance

Compares total electricity demand with hybrid-system supply.

### ⚡ 5. Grid Stability Window

Shows:

* Frequency
* Voltage
* Stable operating bands
* Rolling stability indicators

### 🛡️ 6. Reserve Margin and Renewable Ramp

Shows system flexibility and renewable ramp stress.

### 🌍 7. Carbon Footprint

Shows emissions associated with conventional grid fallback.

### 🦆 8. Duck Curve Mitigation

Compares:

```text
Demand
   vs
Solar-only Net Load
   vs
Solar + Wind Net Load
   vs
Solar + Wind + Hydro Net Load
   vs
Solar + Wind + Hydro + BESS Net Load
```

### 📈 9. Duck Curve Evening Ramp Comparison

Demonstrates the reduction in evening net-load ramp as flexible resources are added.

### 🔋 10. Midday Renewable Surplus & BESS Charging

Shows how excess daytime renewable energy can be stored for later use.

### 📊 11. Peak Evening Ramp Reduction

Compares peak evening ramp under different system configurations.

---

# 📌 Key Performance Indicators

The model calculates:

| KPI                  | Description                                 |
| -------------------- | ------------------------------------------- |
| ⚡ Total Daily Demand | Total simulated electricity demand          |
| ☀️ Solar Energy      | Solar energy dispatched                     |
| 💨 Wind Energy       | Wind energy dispatched                      |
| 🌊 Hydro Energy      | Hydropower dispatched                       |
| 🔋 Battery Energy    | BESS charging/discharging                   |
| 🌱 Renewable Share   | Renewable contribution to demand            |
| 🔌 Fossil Fallback   | Conventional grid support                   |
| 🦆 Duck Curve Depth  | Midday net-load depression                  |
| 📈 Evening Ramp      | Net-load increase after solar decline       |
| 📉 Ramp Reduction    | Reduction due to flexible resources         |
| 🛡️ Reserve Margin   | Available system reserve                    |
| ⚡ Frequency          | Frequency stability indicator               |
| 🔌 Voltage           | Voltage stability indicator                 |
| 🌍 Carbon Footprint  | Estimated conventional-generation emissions |

---

# 🔍 Key System Insights

### ☀️ Solar

Solar PV significantly reduces daytime net load but can contribute to a steep evening net-load ramp as generation decreases.

### 💨 Wind

Wind provides complementary variable renewable generation and can reduce the dependence on solar generation alone.

### 🌊 Hydro

Hydropower provides dispatchable renewable balancing capability and can support the system when variable renewable generation decreases.

### 🔋 BESS

Battery storage absorbs renewable energy during periods of surplus and discharges during higher-demand periods, helping to reduce the evening ramp.

### 🦆 Duck Curve

The combination of Solar + Wind + Hydro + BESS demonstrates how coordinated renewable-energy management can mitigate the net-load effects associated with high solar penetration.

### ⚡ Grid Stability

Reserve margin, frequency, voltage and renewable ramp indicators provide an additional layer of system-level monitoring.

---

# 🧮 Core Energy Balance

The hybrid system follows:

```text
Total Supply =
    Solar
  + Wind
  + Hydro
  + BESS Discharge
  + Conventional Grid Support
```

The renewable contribution is:

```text
Renewable Supply =
    Solar
  + Wind
  + Hydro
  + BESS Discharge
```

And:

```text
Net Load =
    Demand
    − Solar
    − Wind
```

The Duck Curve evening ramp is then evaluated from the change in net load over time.

---

# ⚙️ Technologies Used

```text
🐍 Python
🔢 NumPy
🐼 Pandas
📊 Matplotlib
📄 JSON
📑 CSV
⚡ Energy Management Systems
☀️ Solar PV
💨 Wind Energy
🌊 Hydropower
🔋 Battery Energy Storage
⚡ Grid Stability Analysis
🦆 Duck Curve Analysis
```

---

# 📁 Project Structure

```text
📦 hydro-pv-wind-bess-energy-management-system
│
├── 📜 main.py
│
├── 📁 outputs
│   │
│   ├── 📁 data
│   │   ├── 📊 hourly_hybrid_dispatch.csv
│   │   ├── 📊 duck_curve_analysis.csv
│   │   ├── 📜 metrics_summary.json
│   │   └── 📜 assumptions.json
│   │
│   └── 📁 figures
│       ├── 📊 01_four_source_dispatch.png
│       ├── 💨 02_wind_resource_dispatch.png
│       ├── 🔋 03_battery_soc.png
│       ├── 📈 04_demand_supply_balance.png
│       ├── ⚡ 05_grid_stability_window.png
│       ├── 🛡️ 06_reserve_and_renewable_ramp.png
│       ├── 🌍 07_carbon_footprint.png
│       ├── 🦆 08_duck_curve_mitigation.png
│       ├── 📈 09_duck_curve_ramp_comparison.png
│       ├── 🔋 10_midday_surplus_bess_charging.png
│       └── 📊 11_peak_evening_ramp_reduction.png
│
└── 📜 Oihika_Arpit_Hydro_PV_Wind_BESS_Report.pdf
```

---

# 🚀 How to Run

Clone the repository:

```bash
git clone https://github.com/your-username/hydro-pv-wind-bess-energy-management-system.git
```

Enter the project:

```bash
cd hydro-pv-wind-bess-energy-management-system
```

Install dependencies:

```bash
pip install numpy pandas matplotlib
```

Run the simulation:

```bash
python main.py
```

After execution, generated datasets and figures will be available inside:

```text
outputs/data
outputs/figures
```

---

# 🔮 Future Improvements

The prototype can be further developed through:

* 🌞 Real-time solar irradiance data integration
* 💨 Real wind-speed and wind-turbine datasets
* 🏠 Real smart-meter load profiles
* 🌦️ Seasonal renewable-resource modelling
* 💰 Cost optimization and LCOE analysis
* 🔋 Battery degradation modelling
* 🌊 Seasonal hydropower availability analysis
* ⚡ AC power-flow modelling
* 🛡️ Advanced transient stability analysis
* 🤖 AI-based load forecasting
* 🤖 AI-based renewable generation forecasting
* 🔌 EV charging and Vehicle-to-Grid (V2G)
* 🌐 Smart-grid integration
* 📊 Streamlit interactive EMS dashboard
* 🧠 Model Predictive Control (MPC)
* 📡 Real SCADA data integration

---

# ⚠️ Research & Simulation Disclaimer

This project is an **offline educational and research prototype**.

It does **not** connect to:

* SCADA systems
* PLCs
* Turbine controllers
* Hydropower gates
* Inverters
* Circuit breakers
* Battery management systems
* Utility control systems
* Real-time electrical equipment

The frequency and voltage calculations are **simplified grid-stability indicators** intended for system-level simulation and visualization. They should not be interpreted as validated real-world grid-control or protection calculations.

---

# 👩‍💻 Author

## Oihika Arpit

**Electronics & Communication Engineering**

🌱 Renewable Energy
🌊 Hydropower Systems
☀️ Solar PV
💨 Wind Energy
🔋 Battery Energy Storage
⚡ Smart Grids
📊 Energy Data Science
🤖 AI for Sustainable Energy Systems

---

# 📜 License

This project is licensed under the **MIT License**.

---

## 🌍 Project Vision

> **From renewable generation to intelligent energy management — integrating Solar, Wind, Hydro and Battery Storage for a more flexible and sustainable energy system.**

```text
        ☀️ SOLAR
           +
        💨 WIND
           +
        🌊 HYDRO
           +
        🔋 BESS
           ↓
    🧠 ENERGY MANAGEMENT
           ↓
      🦆 DUCK CURVE
       MITIGATION
           ↓
      ⚡ GRID FLEXIBILITY
           ↓
       🌱 CLEANER
       ENERGY SYSTEMS
```
