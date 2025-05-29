# Characterization of Atmospheric and Surface Physical Properties Inferred by Satellite

**Author:** Antonio Augusto Pilan dos Santos

---

## 📜 Overview

This project presents an undergraduate research study focused on the characterization of atmospheric and surface physical properties using satellite-inferred data. The research investigates estimates of **Land Surface Temperature (LST)** and **Total Precipitable Water (TPW)** in the north-central region of São Paulo state, Brazil. [cite: 8] Data was sourced from the Advanced Baseline Imager (ABI) sensor aboard the GOES-16 geostationary satellite. [cite: 8]

The study addresses the following scientific questions: "How do surface temperature and atmospheric water vapor over north-central São Paulo statistically characterize themselves from satellite inferences? [cite: 10] What are the limitations of this technique?" [cite: 10]

This work highlights the potential of using GOES-16 data to analyze significant socio-economic and environmental impacts, such as droughts and heatwaves, in a key region of São Paulo. [cite: 14, 16]

---

## 🎯 Objectives

The main objectives of this research were:

* To characterize the daily average Land Surface Temperature (LST) in the interior region of São Paulo state. [cite: 46]
* To characterize the daily average Total Precipitable Water (TPW) in the same region. [cite: 46]
* To perform representative sampling of the obtained data. [cite: 47]
* To understand the remote sensing techniques, their physical aspects, advantages, disadvantages, and potential methods to address limitations. [cite: 47]

---

## 🛠️ Methodology and Technical Stack

### Data Source and Tools
* **Satellite Data**: Measurements were obtained from the Advanced Baseline Imager (ABI) sensor on the **GOES-16** satellite. [cite: 8] This satellite provides high-frequency radiance measurements (every 10 minutes) with a spatial resolution of up to 2km. [cite: 9, 53]
* **Data Products**:
    * `ABI-L2-LSTF` / `ABI-L2-LSTF2KM`: Land Surface Temperature (Full Disk / 2km resolution). [cite: 58, 59]
    * `ABI-L2-TPWF`: Total Precipitable Water (Full Disk). [cite: 58, 59]
* **Data Access**: GOES-16 data was accessed via **Amazon Web Services (AWS)**. [cite: 54, 96]
* **Programming Language and Libraries**:
    * **Python** was the primary language for data processing and analysis. [cite: 96]
    * `s3fs`: Used for accessing data on AWS. [cite: 96]
    * `XArray`: For structuring and handling multidimensional data (x, y, intensity). [cite: 98]
    * `Pyproj`: For performing cartographic projections (latitude/longitude calculations) using the WGS84 model. [cite: 100]
    * The complete code and data processing pipeline are detailed in a Google Colab notebook: [Link to Google Colab Notebook] [cite: 102]

### Study Area and Sampling
* **Region**: A 200km x 200km square area in the interior of São Paulo state, centered around Ribeirão Preto. [cite: 109] This region was chosen for its socioeconomic importance in agriculture and to minimize geographical interferences like large rivers or frequent cloud cover.
* **Sampling Strategy**: Data was consistently evaluated at **15:00 UTC** (12:00 Brasília time) daily to ensure comparability and minimize cloud influence. [cite: 110]
* **Data Quality**: Only readings with over 70% valid pixels (i.e., less than 30% cloud cover) were considered for statistical analysis[cite: 117], acknowledging a potential bias towards clearer, possibly warmer and drier days. [cite: 118, 119] Linear interpolation was used to handle missing data for short intervals. [cite: 141]

### Physical Principles
* **Land Surface Temperature (LST)**: Inferred using the $11.2\mu m$ and $12.3\mu m$ channels (atmospheric window), which are transparent or semi-transparent to the atmosphere. [cite: 63, 64, 65] The algorithm considers emitted surface radiance ($I_{s}(\lambda)$), reflected atmospheric radiance ($I_{atm}^{\perp}(\lambda)$), and upwelling atmospheric radiance ($I_{atm}^{\dagger}(\lambda)$), applying Planck's Law to derive temperature ($T_s$) from spectral radiance ($B(\lambda,T_{s})$). [cite: 66, 67, 69] Surface masking for water, clouds, and ice is applied to ensure only land temperature is measured. [cite: 74, 75]
* **Total Precipitable Water (TPW)**: Estimated by projecting all water vapor in the atmospheric column onto the ground, measured in centimeters. [cite: 78] The algorithm discretizes the atmosphere into layers ($k$) and uses specific GOES-16 channels sensitive to water vapor absorption ($q_k$) at different altitudes. [cite: 79, 80] It employs numerical integration and Look-Up Tables (LUTs) relating radiance to water vapor content to build a vertical profile and then integrate it using the formula: $TPW = \frac{10}{\rho_{w}g}\sum0.5*(q_{k+1}+q_{k})*(p_{k}-p_{k+1})$. [cite: 86, 87, 88, 89]

---

## 📊 Key Findings and Results

### Land Surface Temperature (LST)
* The study successfully characterized LST, revealing distinct geographical distributions and temporal trends. [cite: 123] For instance, on August 13, 2022, the average temperature in the defined area was 309.89 K. [cite: 129]
* The methodology allowed for the identification of phenomena such as heatwaves and the impact of smoke from wildfires on LST. [cite: 133] Smoke plumes were observed to lower LST readings significantly by blocking solar radiance. [cite: 135, 136]
* Comparative analysis of August LST over 2022, 2023, and 2024 showed that August 2024 was notably warmer, with median temperatures higher than the preceding two years. [cite: 146, 150] This coincided with extensive wildfires in the region. [cite: 154, 155, 156, 157, 158]
* Annual LST trends indicated a general increase in temperatures throughout the year, peaking around August. [cite: 161] The year 2024 showed atypically higher temperatures compared to 2022 and 2023. [cite: 162, 163]

### Total Precipitable Water (TPW)
* TPW analysis revealed characteristic seasonal patterns, with a pronounced drop in atmospheric water vapor around day 100 of each year (March-April), leading to extended dry periods. [cite: 168, 169]
* The year 2024 was identified as atypically dry. [cite: 171] A significant second drop in TPW occurred around day 200 (approaching July). [cite: 170]
* The combination of high temperatures and low TPW in 2024, particularly the low TPW values (around 5cm) during the August heatwave, created conditions highly conducive to the observed large-scale wildfires. [cite: 170, 175, 176]

### Correlation and Impact
* A strong correlation was observed between LST, TPW, and drought periods[cite: 15], particularly highlighting the conditions leading to the 2024 wildfires. [cite: 170]
* The study demonstrates that GOES-16 satellite data can effectively monitor and analyze environmental conditions with significant socio-economic implications. [cite: 16, 185]

---

## ✨ Conclusions

This research successfully characterized the daily average LST and TPW in the north-central São Paulo region, demonstrating clear annual trends and seasonal patterns. [cite: 177, 178] Temperatures tend to rise throughout the year, peaking in August[cite: 177], while TPW shows distinct wet and dry periods. [cite: 178]

**Advantages of the Technique:**
* Good correlation between GOES-16 data and observed regional phenomena. [cite: 180]
* Provides a viable, often the only economically feasible, method for certain types of environmental studies. [cite: 197]
* Can be a powerful tool for monitoring and potentially anticipating events with significant environmental and economic impact, especially when combined with local data. [cite: 196, 198]

**Limitations and Biases:**
* **Cloud Contamination**: The pre-selection against cloud-covered pixels (and other white surfaces) introduces a bias towards warmer and drier conditions, as cloudy days (generally cooler and moister) are excluded. [cite: 181, 182] Linear interpolation for short gaps is a reasonable but limited mitigation. [cite: 183]
* **Algorithm Accuracy**: While LST physics is more direct[cite: 184], TPW relies on inferences from pre-calculated tables and can have variable point-to-point accuracy[cite: 184], though overall trends are consistent with observed phenomena. [cite: 185]

The standardized sampling methodology was crucial for achieving successful data characterization. [cite: 187] The findings for 2024, showing an atypically hot and dry year, suggest that early warning signs of severe drought and heightened fire risk could have been identified by July 2024 with active monitoring. [cite: 186]

---

## 🚀 Future Work

Potential avenues for further research include:

* Investigating the suspected temperature gradient within the study region and its geographical correlation with TPW. [cite: 189]
* Analyzing the relationship between these LST/TPW patterns and the incidence of wildfires, potentially using the GOES-16 fire detection product (ABI-L2-FDCF). [cite: 190, 191]
* Adopting different sampling strategies, such as separating analyses for distinct wet and dry periods, to refine understanding and potentially characterize TPW algorithm error by season. [cite: 192, 193, 194, 195]
* Developing robust monitoring and prediction networks by integrating satellite data with local ground-based measurements. [cite: 198]

---

## 🔗 Links

* **Research Paper (PDF)**: [Link to `Caracterização_de_propriedades_físicas_atmosféricas_e_de_superfície_inferidas_por_satélite.pdf` in your repository]
* **Google Colab Notebook (Code)**: [Link para o Google Collab] [cite: 102]
* **GitHub Repository**: [https://github.com/antonio-pilan/TCC-Geosensing-Dataprocessing-USP](https://github.com/antonio-pilan/TCC-Geosensing-Dataprocessing-USP)

---

## 🔑 Keywords

Atmospheric Physics, Remote Sensing, Satellite GOES-16, Drought Periods, Wildfires, Land Surface Temperature (LST), Total Precipitable Water (TPW), Data Science, Python, AWS. [cite: 17]

---

## 📄 License

Please specify the license under which this project is shared (e.g., MIT, GPL, etc.). You can add a `LICENSE` file to your repository.

---

*This README was generated based on the research paper "Caracterização de propriedades físicas atmosféricas e de superfície inferidas por satélite" by Antonio Augusto Pilan dos Santos, São Carlos, 2024.*
