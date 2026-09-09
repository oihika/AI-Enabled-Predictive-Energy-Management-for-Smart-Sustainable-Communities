# hydro-pv-bess-energy-management-system
Python-based simulation of a hybrid hydro-PV-battery energy management system with SCADA-inspired monitoring, renewable dispatch analysis and carbon-footprint evaluation.

# ⚡ Jabalpur Hydro-Solar-Battery Hybrid Energy Simulation as a prototype example

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange.svg)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Domain](https://img.shields.io/badge/Domain-Renewable%20Energy-red.svg)

---

## 🌞 Project Overview

This project presents a Python-based simulation of a **hybrid renewable energy system for Jabalpur, India**, integrating:

- ☀️ Solar photovoltaic generation  
- 🔋 Battery energy storage  
- ⚡ Hydropower reserve inspired by Rani Avanti Bai Hydel Power Station  
- 🔌 Fossil grid fallback for unmet demand  

The system simulates a 24-hour energy dispatch strategy that prioritizes renewable energy sources and reduces dependence on non-renewable grid backup.

---

## 🏗️ System Architecture

```text
        ☀️ Solar PV Generation
                 ↓
        ⚡ Energy Dispatch Logic
          ↙        ↓        ↘
   🔋 Battery   ⚡ Hydro   🔌 Fossil Backup
          \        |        /
           → 🏠 Load Demand


🧠 Methodology
The simulation follows a rule-based dispatch priority:

Solar power supplies load first
Excess solar charges the battery
Battery discharges during demand deficit
Hydropower operates as renewable backup
Fossil fallback is used only when all renewable sources are insufficient
The project also models:

Battery state of charge
Hydro dispatch availability
Hourly demand-supply balance
Carbon emissions from fossil fallback
SCADA-inspired hydropower operating indicators
⚡ Hydropower Reference Values
The hydropower model is inspired by reference readings from Rani Avanti Bai Hydel Power Station.

Parameter	Value
Active Power	34.10 MW
Generator Voltage	11 kV
Frequency	50 Hz
Reservoir Level	409.55 m
Effective Head	39.85 m
Water Discharge	97.5 m³/s
Gate Opening	56.25%
Generator RPM	166.6
This is an offline educational simulation only. It does not connect to any real SCADA, PLC, turbine, gate, inverter, breaker, battery controller, or electrical equipment.

📁 Project Structure
📦 jabalpur-hydro-solar-battery-hybrid
┣ 📜 main.py
┣ 📜 README.md
┣ 📁 outputs
┃ ┣ 📁 data
┃ ┃ ┣ 📜 hourly_hybrid_dispatch.csv
┃ ┃ ┣ 📜 metrics_summary.json
┃ ┃ ┗ 📜 assumptions.json
┃ ┗ 📁 figures
┃   ┣ 📊 01_generation_by_source.png
┃   ┣ 📊 02_battery_soc.png
┃   ┣ 📊 03_demand_vs_supply.png
┃   ┗ 📊 04_carbon_footprint.png
┗ 📜 Oihika_Arpit_IEEE_Hydro_Solar_Battery_MVP_Report.pdf
📊 Results & Visualizations
⚡ Hourly Generation by Source


🔋 Battery State of Charge


📈 Demand vs Hybrid Supply


🌍 Carbon Footprint


📌 Key Results
Metric	Result
Total Daily Demand	1061.00 MWh
Solar Direct to Load	347.31 MWh
Solar Charged to Battery	33.24 MWh
Battery Delivered	53.28 MWh
Hydro Dispatched	479.84 MWh
Fossil Fallback	180.57 MWh
Renewable Supply	82.98%
Carbon Footprint	148,063.60 kg CO₂
Final Battery SOC	7.00 MWh / 10.00%
Hours Hydro Dispatched	18
Hours Fossil Fallback Used	8
🔍 Key Insights
Solar energy contributes strongly during daytime demand periods
Battery storage helps shift solar energy into low-generation hours
Hydropower acts as a reliable renewable reserve when solar and battery are insufficient
Evening peak demand remains the main driver of fossil fallback usage
The hybrid system achieves approximately 83% renewable supply in the simulated day
⚙️ Technologies Used
Python
NumPy
Pandas
Matplotlib
JSON
CSV-based simulation outputs
🚀 How to Run
git clone https://github.com/your-username/jabalpur-hydro-solar-battery-hybrid.git
cd jabalpur-hydro-solar-battery-hybrid
pip install numpy pandas matplotlib
python main.py
After running the program, output files will be generated inside:

outputs/data
outputs/figures
🔮 Future Improvements
Real solar irradiance data integration
Real smart meter load profile
Cost optimization and LCOE analysis
Battery degradation modeling
Seasonal hydropower availability analysis
Streamlit dashboard for real-time visualization
AI-based load forecasting
👨‍💻 Author
Oihika Arpit
Electronics & Communication Engineering
Renewable Energy, Hydropower Systems & Data Science Enthusiast

📜 License
This project is licensed under the MIT License.
```
