# Delhi Air Quality & EV Adoption Digital Twin (2025–2040)

## 🎯 Project Overview
This project is a **System Dynamics simulation** built in Vensim to evaluate the long-term impact of various Electric Vehicle (EV) adoption strategies on Delhi’s air quality. The model acts as a "Digital Twin" of the city’s transportation and environmental sectors, quantifying the relationship between policy mandates, vehicular fleet turnover, and public health costs.

---

## 🏗️ Model Architecture
The simulation is built on three interconnected sectors:

### 1. Transportation Sector
* **Total Vehicles (Stock):** Tracks the accumulation of the city's fleet, starting from a baseline of ~14.3 million vehicles.
* **Fleet Turnover:** Models growth (5% annual purchase rate) and scrappage (average 12-year vehicle lifespan).
* **Technology Diffusion:** Uses an **S-Curve model** via Lookup tables to represent the non-linear adoption of EVs across the population.

### 2. Environmental Sector (PM2.5)
* **Pollution Generation:** Calculates the daily emission load based on vehicle count, emission factors ($g/km$), and adoption fraction.
* **Seasonal Variation (Weather):** Implements a **Sinusoidal function** for the `Natural_Dissipation_Fraction` to simulate Delhi's winter smog episodes and monsoon clearing.

### 3. Socio-Economic Impact
* **Cumulative Health Cost (Stock):** Integrates the annual health expenditure driven by PM2.5 levels, translating environmental data into economic terms.

---

## 🧪 Scenario Analysis
The project evaluates two primary scenarios using a `Policy_Switch` toggle:

| Feature | **Business as Usual (BAU)** | **Aggressive Green (Policy 2.0)** |
| :--- | :--- | :--- |
| **Logic** | Natural market momentum. | Radical government intervention. |
| **2027 Target** | ~5% share of new sales. | **95% of new registrations electric**. |
| **2040 Outcome** | Partial fleet electrification (~25%). | Near-total zero-emission fleet (~95%). |

---

## 📈 Key Technical Findings
* **Adoption Latency:** The simulation demonstrates that even if 95% of *new* sales are electric by 2027, the *total fleet share* takes significantly longer to transition due to the stock of legacy internal combustion engine (ICE) vehicles.
* **Policy Sensitivity:** Scrappage enforcement is shown to be a more powerful lever for immediate air quality improvement than purchase subsidies alone.
* **Seasonal Volatility:** Despite aggressive EV growth, high winter PM2.5 peaks persist until the total fleet share crosses a critical mass threshold.



---

## 🛠️ How to Run
1.  **Download the Model:** Open the `Delhi_Pollution_Model.mdl` file in Vensim PLE or higher.
2.  **Configure Scenarios:** * Set `Policy_Switch = 0` for the BAU baseline.
    * Set `Policy_Switch = 1` for the Aggressive Green scenario.
3.  **Simulation:** Click the **Simulate** button to run the engine.

---

## 📜 Equation Reference
| Variable | Formula / Logic |
| :--- | :--- |
| **Vehicle Purchase Rate** | `Total_Vehicles * Annual_Growth_Rate` |
| **Pollution Generation** | `(Vehicles * (1 - EV_Fraction) * Emission_Factor * Distance) / 1000000` |
| **Health Expenditure** | `PM2.5_Concentration * Cost_Per_Microgram` |
| **Natural Dissipation** | `Baseline + (Amplitude * SIN( 6.28 * Time / 1 ))` |

---
