# Project: Individual Household Power Consumption Forecasting with LSTM

## Step 1: Data Gathering

### Objective
The objective of this step is to develop a dataset that closely reflects the power consumption patterns of Indian households. Since publicly available datasets rarely capture the diversity of Indian electricity usage, we created a synthetic dataset that combines realistic consumption trends, household behaviors, and seasonal influences.

---

### Dataset Overview
<<<<<<< HEAD
For this project, a synthetic dataset was generated, consisting of **400,000 unique rows**. Each entry records the household’s electricity consumption over time, along with additional contextual features to capture patterns more effectively.

**Key Attributes Included:**
- **Global_active_power**: Total active power consumption (kW)
- **Global_reactive_power**: Reactive power consumption (kVAR)
- **Voltage**: Voltage across the household mains (Volts)
- **Global_intensity**: Total current usage (Ampere)
- **Sub_metering_1**: Energy used in kitchen appliances (kWh)
- **Sub_metering_2**: Energy used in laundry appliances (kWh)
- **Sub_metering_3**: Energy used by AC and water heaters (kWh)
- **Datetime**: Timestamp in `YYYY-MM-DD HH:MM:SS` format
- **hour**, **day_of_week**, **month**: Time-related features for trend analysis
- **is_weekend**: Weekend indicator (1 = Weekend, 0 = Weekday)
- **is_holiday**: Festival/holiday indicator relevant to the Indian calendar
=======
For this project, a synthetic dataset was generated, consisting of *400,000 unique rows*. Each entry records the household’s electricity consumption over time, along with additional contextual features to capture patterns more effectively.

*Key Attributes Included:*
- *Global_active_power*: Total active power consumption (kW)
- *Global_reactive_power*: Reactive power consumption (kVAR)
- *Voltage*: Voltage across the household mains (Volts)
- *Global_intensity*: Total current usage (Ampere)
- *Sub_metering_1*: Energy used in kitchen appliances (kWh)
- *Sub_metering_2*: Energy used in laundry appliances (kWh)
- *Sub_metering_3*: Energy used by AC and water heaters (kWh)
- *Datetime*: Timestamp in YYYY-MM-DD HH:MM:SS format
- *hour, **day_of_week, **month*: Time-related features for trend analysis
- *is_weekend*: Weekend indicator (1 = Weekend, 0 = Weekday)
- *is_holiday*: Festival/holiday indicator relevant to the Indian calendar
>>>>>>> f6c165f5ea3c95d1da97a5ff45a290253b168858

---

### Approach to Data Generation

Given the absence of open-source datasets reflecting Indian consumption behavior, we focused on generating data that feels as close to real-world patterns as possible.

#### Considerations:
<<<<<<< HEAD
- **Time-of-Day Variations**: Higher usage during morning and evening peak hours.
- **Seasonal Trends**: Increased consumption during summer months due to cooling appliances.
- **Weekend & Holiday Effects**: Different usage behavior during weekends and major festivals like Diwali, Holi, Eid, etc.
- **Voltage Fluctuations**: Simulated voltage ranges (220V–250V) based on Indian power supply norms.

#### Methodology:
- **Global_active_power** was created to show higher values during peak hours (morning and evening) and lower values during the night, just like in a typical household.
- **Voltage and reactive power** were generated using common value ranges seen in Indian homes, with slight randomness to make the data more realistic.
- **Sub-meterings** (energy used in kitchen, laundry, and AC/heater areas) were distributed based on common appliance usage in Indian families.
- **Datetime features** like hour, day of the week, and month were automatically added to reflect daily and seasonal usage habits, including weekends and festival holidays.
=======
- *Time-of-Day Variations*: Higher usage during morning and evening peak hours.
- *Seasonal Trends*: Increased consumption during summer months due to cooling appliances.
- *Weekend & Holiday Effects*: Different usage behavior during weekends and major festivals like Diwali, Holi, Eid, etc.
- *Voltage Fluctuations*: Simulated voltage ranges (220V–250V) based on Indian power supply norms.

#### Methodology:
- *Global_active_power* was created to show higher values during peak hours (morning and evening) and lower values during the night, just like in a typical household.
- *Voltage and reactive power* were generated using common value ranges seen in Indian homes, with slight randomness to make the data more realistic.
- *Sub-meterings* (energy used in kitchen, laundry, and AC/heater areas) were distributed based on common appliance usage in Indian families.
- *Datetime features* like hour, day of the week, and month were automatically added to reflect daily and seasonal usage habits, including weekends and festival holidays.
>>>>>>> f6c165f5ea3c95d1da97a5ff45a290253b168858

---

### Why Synthetic Data?
<<<<<<< HEAD
- No single open dataset captures **Indian-specific consumption habits**.
- Creating synthetic data allowed for **customization**, ensuring it reflects:
=======
- No single open dataset captures *Indian-specific consumption habits*.
- Creating synthetic data allowed for *customization*, ensuring it reflects:
>>>>>>> f6c165f5ea3c95d1da97a5ff45a290253b168858
   - Typical urban middle-class consumption
   - Seasonal and festive variations
   - Time-of-day trends
- All assumptions were based on observed patterns from Indian utility studies and appliance usage reports.

---

### Summary
<<<<<<< HEAD
This dataset serves as a solid foundation for training and evaluating LSTM models for electricity consumption forecasting in an Indian household setting. The structured design of the dataset ensures it captures temporal trends and realistic variability crucial for deep learning models.

---
=======
This dataset serves as a solid foundation for training and evaluating LSTM models for electricity consumption forecasting in an Indian household setting. The structured design of the dataset ensures it captures temporal trends and realistic variability crucial for deep learning models.
>>>>>>> f6c165f5ea3c95d1da97a5ff45a290253b168858
