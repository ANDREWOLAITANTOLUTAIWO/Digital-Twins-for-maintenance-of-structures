INTRODUCTION
Temperature in the environment of a building is considered one of the major factors for accurately predicting energy use in the building (Košir et al., 2018, Park et al., 2020). Studies have shown that land surface temperature (LST) significantly impacts energy use in buildings as it increases building cooling energy use and decreases building heating energy use (Singh and Sharston, 2022). LST is a measure of how hot the land is to the touch. LST is different from surface air temperature (SAT), also called ambient temperature, which is the temperature of the environment above the ground surface. Outdoor and indoor temperature have been established as fundamental factors that influence energy use in buildings (Lee and Lee, 2009), which can be managed with digital twin technology. 

Digital Twins (DT), a technology that integrates 3D models with data from geospatial technologies, internet-of-things, sensors, big data analytics, machine learning, artificial intelligence and virtual reality, is an advanced tool for modeling, predicting and mitigating impacts of change in a product or process.

By simulating different scenarios, DT can forecast the future performance of buildings and suggest optimal maintenance schedules. This approach reduces downtime maintenance, extends the lifespan of assets, and ultimately leads to significant cost savings (Jones et al., 2020). By offering comprehensive insights into energy use patterns, digital twins contribute significantly to sustainability efforts, enabling building managers to identify areas of energy wastage and implement corrective measures to reduce their carbon footprint. One of the most substantial advantages of digital twins is their ability to facilitate predictive maintenance. By continuously monitoring building systems and analyzing real-time data, digital twins can anticipate potential issues before they escalate into serious problems, allowing for proactive maintenance interventions that minimize downtime, extend the lifespan of equipment, and significantly reduce maintenance costs. Case studies have demonstrated substantial cost reductions and energy savings through the implementation of digital twin technology in building management.  

DT has found significant applications in the monitoring, control, and optimization of heating, ventilation and air conditioning (HVAC) systems, which are major energy consumers in buildings. By creating virtual models of HVAC units and integrating real-time data on parameters such as temperature, airflow, pressure, and energy use, digital twins enable HVAC professionals to simulate various operating conditions, analyze performance, predict potential failures, and optimize settings for maximum efficiency. This proactive approach allows for the prediction of maintenance needs, reducing unplanned downtime and extending the lifespan of equipment. 
This study aims to implement a DT to simulate various operating conditions, analyze performance, and predict potential failures of HVAC as it responds to increase in indoor temperature as a result of increase in LST. We used Python codes to simulate a DT of the HVAC in Nigerian Institution of Surveyors (NIS) building, and study the impact of temperature rise on energy use in the building. 

METHODOLOGY 
Dataset
1. Indoor temperature, collected with thermometer. 
2. Electric energy in KWh used in the building from 2015 to 2025, collected from Ikeja Electricity Distribution Company. 
3. Monthly surface air temperature (SAT) between 2015 and 2025, collected from Nigerian meteorological Agency (NiMeT) at a meteorological station in the Lagos Airport. 
4. Monthly Land Surface Temperature (LST) between 2015 and 2025 of Ikeja Lagos extracted from Landsat-8 imageries in RSLab at https://rslab.gr/Landsat_LST.html 

Data Collection
Indoor temperature of NIS building was collected from the company managing the building. The HVAC systems log indoor temperature of the building. LST data of the building environment for 2015 to 1025 was collected from RSLab. RSLab is a web application that explores the estimation of land surface temperature (LST) for the globe from Landsat 5, 7 and 8 thermal infrared sensors, using different surface emissivity sources. The algorithm is based on the Google Earth Engine (GEE), which allows the estimation of LST products for the globe, covering the time period from 1984 to present (Parastatidis, 2017). For the purpose of this study, landsat-8 was chosen as the imagery form which LST was extracted, and NDVI-based emissivity was used. 

Digital Twin Logic
The DT model was coded in Google CoLab. We created a variable Delta_T (LST − I_Temp). This teaches the model that it is not just about "heat," but about how hard the cooling system has to work to fight the outside heat. Since we do not have live sensors, we used Time-Step Simulation (PowerWorld, 2014). We treat our historical data (2015–2025) as if it is streaming in right now, month by month. This allows us to replay history and see how our DT would have reacted to changes in the environment. Instead of a live feed from a sensor, our Python script becomes the "feed" following these steps:
Step 1: The script reads the first month’s data row.
Step 2: It calculates the predicted energy.
Step 3: It compares with actual energy needed to cool the building.
Step 4: It raises alerts if the energy difference is beyond a threshold.
Step 5: It waits for 2 seconds (simulated delay), then reads next month’s data.
Step 6: It repeats the process from step 2.

It uses time.sleep() to simulate the feeling of real-time data arriving, and prints a "Live Log" of the building's energy status. If the actual energy is 5% higher than predicted energy, the system raises ALERT. If it is less than -5%, the system comments that the HVAC performance is GOOD and saving energy. Otherwise, it comments that the HVAC is performance is NORMAL. Thus, a static file is turned into a dynamic DT of the building's energy performance. 

RESULTS
Output of Digital Twin Simulation for the months in 2015
The result of simulating the Digital Twin for 2015 is shown in Figure 3 and Figure 4. The simulation is visualized in Figure 4, which shows what the DT energy performance looks like when fed with the dataset. Blue line (reality) is the actual energy bill. Orange dashed line (The DT) is what the model predicted the energy should be, based on the LST and Indoor Temperature for that month. Notice where the blue line goes 5% higher than the orange line. That gap represents inefficiency or waste. The DT instantly flags this. 

Simulating “What-if” Scenarios
We can manually change the values in the code to test hypotheses. For example, What if we installed better windows (lowering the effect of LST)? For instance, we can reduce Delta_T by 10% to simulate better insulation. This allows us to calculate the potential energy savings we could have achieved in those months without spending money on really constructing insulation systems. 

CONCLUSION
This study simulated Digital Twin for energy performance in NIS building. The system signifies when the energy consumption in the building is below a threshold of 10% tolerance. The system raises alert when the difference between actual energy consumption and predicted energy is above the tolerance. Scenarios of better insulation in the building can be tested to see how much energy it takes to improve thermal comfort in the building without spending money on real construction. 
