# Characterization of Atmospheric and Surface Physical Properties Inferred by Satellite

**Author:** Antonio Augusto Pilan dos Santos

---

## 📜 Overview

This project presents an undergraduate research study focused on the characterization of atmospheric and surface physical properties using satellite-inferred data. The research investigates estimates of **Land Surface Temperature (LST)** and **Total Precipitable Water (TPW)** in the north-central region of São Paulo state, Brazil. Data was sourced from the Advanced Baseline Imager (ABI) sensor aboard the GOES-16 geostationary satellite. 

The study addresses the following scientific questions: "How do surface temperature and atmospheric water vapor over north-central São Paulo statistically characterize themselves from satellite inferences? What are the limitations of this technique?" 

This work highlights the potential of using GOES-16 data to analyze significant socio-economic and environmental impacts, such as droughts and heatwaves, in a key region of São Paulo. 

---

## 🎯 Objectives

The main objectives of this research were:

* To characterize the daily average Land Surface Temperature (LST) in the interior region of São Paulo state. 
* To characterize the daily average Total Precipitable Water (TPW) in the same region. 
* To perform representative sampling of the obtained data. 
* To understand the remote sensing techniques, their physical aspects, advantages, disadvantages, and potential methods to address limitations.

---

## 🛠️ Methodology and Technical Stack

### Data Source and Tools
* **Satellite Data**: Measurements were obtained from the Advanced Baseline Imager (ABI) sensor on the **GOES-16** satellite.This satellite provides high-frequency radiance measurements (every 10 minutes) with a spatial resolution of up to 2km.
* **Data Products**:
    * `ABI-L2-LSTF` / `ABI-L2-LSTF2KM`: Land Surface Temperature (Full Disk / 2km resolution). 
    * `ABI-L2-TPWF`: Total Precipitable Water (Full Disk).
* **Data Access**: GOES-16 data was accessed via **Amazon Web Services (AWS)**.
* **Programming Language and Libraries**:
    * **Python** was the primary language for data processing and analysis.
    * `s3fs`: Used for accessing data on AWS.
    * `XArray`: For structuring and handling multidimensional data (x, y, intensity). 
    * `Pyproj`: For performing cartographic projections (latitude/longitude calculations) using the WGS84 model.
    * The complete code and data processing pipeline are detailed in a Google Colab notebook: 

### Study Area and Sampling
* **Region**: A 200km x 200km square area in the interior of São Paulo state, centered around Ribeirão Preto. This region was chosen for its socioeconomic importance in agriculture and to minimize geographical interferences like large rivers or frequent cloud cover.
* **Sampling Strategy**: Data was consistently evaluated at **15:00 UTC** (12:00 Brasília time) daily to ensure comparability and minimize cloud influence.
* **Data Quality**: Only readings with over 70% valid pixels (i.e., less than 30% cloud cover) were considered for statistical analysis, acknowledging a potential bias towards clearer, possibly warmer and drier days. Linear interpolation was used to handle missing data for short intervals.

### Physical Principles
* **Land Surface Temperature (LST)**: Inferred using the $11.2\,\mu\text{m}$ and $12.3\,\mu\text{m}$ channels (atmospheric window), which are transparent or semi-transparent to the atmosphere. The algorithm considers emitted surface radiance $I_{s}(\lambda)$, reflected atmospheric radiance $I_{atm}^{\perp}(\lambda)$, and upwelling atmospheric radiance $I_{atm}^{\dagger}(\lambda)$, applying Planck's Law to derive temperature $T_{s}$ from spectral radiance $B(\lambda,T_{s})$. Surface masking for water, clouds, and ice is applied to ensure only land temperature is measured.
* **Total Precipitable Water (TPW)**: Estimated by projecting all water vapor in the atmospheric column onto the ground, measured in centimeters. The algorithm discretizes the atmosphere into layers $k$ and uses specific GOES-16 channels sensitive to water vapor absorption $q_{k}$ at different altitudes. It employs numerical integration and Look-Up Tables (LUTs) relating radiance to water vapor content to build a vertical profile and then integrate it using the formula:
    $TPW = \frac{10}{\rho_{w}g}\sum 0.5 \cdot (q_{k+1} + q_{k}) \cdot (p_{k} - p_{k+1})$

---

## 📊 Key Findings and Results

### Land Surface Temperature (LST)
* The study successfully characterized LST, revealing distinct geographical distributions and temporal trends. For instance, on August 13, 2022, the average temperature in the defined area was 309.89 K.
* The methodology allowed for the identification of phenomena such as heatwaves and the impact of smoke from wildfires on LST. Smoke plumes were observed to lower LST readings significantly by blocking solar radiance.
* Comparative analysis of August LST over 2022, 2023, and 2024 showed that August 2024 was notably warmer, with median temperatures higher than the preceding two years.This coincided with extensive wildfires in the region.
* Annual LST trends indicated a general increase in temperatures throughout the year, peaking around August. The year 2024 showed atypically higher temperatures compared to 2022 and 2023.

### Total Precipitable Water (TPW)
* TPW analysis revealed characteristic seasonal patterns, with a pronounced drop in atmospheric water vapor around day 100 of each year (March-April), leading to extended dry periods.
* The year 2024 was identified as atypically dry. A significant second drop in TPW occurred around day 200 (approaching July).
* The combination of high temperatures and low TPW in 2024, particularly the low TPW values (around 5cm) during the August heatwave, created conditions highly conducive to the observed large-scale wildfires.
  
### Correlation and Impact
* A strong correlation was observed between LST, TPW, and drought periods, particularly highlighting the conditions leading to the 2024 wildfires.
* The study demonstrates that GOES-16 satellite data can effectively monitor and analyze environmental conditions with significant socio-economic implications.

---

## ✨ Conclusions

This research successfully characterized the daily average LST and TPW in the north-central São Paulo region, demonstrating clear annual trends and seasonal patterns. Temperatures tend to rise throughout the year, peaking in August, while TPW shows distinct wet and dry periods.

**Advantages of the Technique:**
* Good correlation between GOES-16 data and observed regional phenomena.
* Provides a viable, often the only economically feasible, method for certain types of environmental studies.
* Can be a powerful tool for monitoring and potentially anticipating events with significant environmental and economic impact, especially when combined with local data.

**Limitations and Biases:**
* **Cloud Contamination**: The pre-selection against cloud-covered pixels (and other white surfaces) introduces a bias towards warmer and drier conditions, as cloudy days (generally cooler and moister) are excluded. Linear interpolation for short gaps is a reasonable but limited mitigation.
* **Algorithm Accuracy**: While LST physics is more direct, TPW relies on inferences from pre-calculated tables and can have variable point-to-point accuracy, though overall trends are consistent with observed phenomena.

The standardized sampling methodology was crucial for achieving successful data characterization. The findings for 2024, showing an atypically hot and dry year, suggest that early warning signs of severe drought and heightened fire risk could have been identified by July 2024 with active monitoring.

---

## 🚀 Future Work

Potential avenues for further research include:

* Investigating the suspected temperature gradient within the study region and its geographical correlation with TPW.
* Analyzing the relationship between these LST/TPW patterns and the incidence of wildfires, potentially using the GOES-16 fire detection product (ABI-L2-FDCF). 
* Adopting different sampling strategies, such as separating analyses for distinct wet and dry periods, to refine understanding and potentially characterize TPW algorithm error by season.
* Developing robust monitoring and prediction networks by integrating satellite data with local ground-based measurements.

---

## 🔑 Keywords

Atmospheric Physics, Remote Sensing, Satellite GOES-16, Drought Periods, Wildfires, Land Surface Temperature (LST), Total Precipitable Water (TPW), Data Science, Python, AWS.
