\--- **WORKFLOW FOR SIMULATIONS AND DATA ANALYSIS** ---



**Article**: Towards Understanding Electrolyte Salt Inhomogeneities in Lithium-ion Batteries: A Multiscale Model Based on Electrolyte Motion and Poroelasticity

**Author**: Johannes Bakkelund

**Contact**: johannes.bakkelund@uia.no, williams.a.appiah@uia.no

**Affiliation**: University of Agder, Faculty of Engineering and Science, Grimstad, 4879, Agder, Norway

**Date**: 10/04/2026



\--------------------------------------------------


## User Guidelines ##


**Repository description**
This toolbox contains the workflow for running COMSOL simulations and reproducing plots and data analysis detailed in the article "Towards Understanding Electrolyte Salt Inhomogeneities in Lithium-ion Batteries: A Multiscale Model Based on Electrolyte Motion and Poroelasticity". The COMSOL model is a macroscale electrochemical-thermal-poroelastic model used to simulate the operation of a LG MJ1 18650 cells, including electrochemical transport and reactions, temperature evolution, and most importantly: the mechanical response of active material expansion leading to electrolyte motion. Repeated cell cycling is simulated, which leads to electrolyte motion induced salt inhomogeneity (EMSI) and capacity fade. The data produced by the simulation in COMSOL is automatically exported as CSV-files and analyzed using the Python scripts in this repository.


**1. Running COMSOL simulations**



The COMSOL file is located at "/COMSOL/EMSI\_model\_V1\_batch\_sweep.mph" with password "Battery\_Coast\_26", containing the macroscale continuum model with model parameters given in tables A1-A3 in the article. The mph file runs a batch sweep with the simulations used to generate data for the article (different c-rates, temperatures, permeabilities etc.), the output directory is set to the standard COMSOL outdir, typically "\~/Documents/COMSOL/Batch". The full batch sweep takes roughly 12 hours running on a AMD Epyc-milan processor with 64 cores and 258GiB memory, and after completion the relevant data from the simulations are automatically exported as csv-files in the output directory. These data files have been computed beforehand and can be found in "/raw\_data".



**2. Analyzing and plotting data**



The data generated from COMSOL simulations are analyzed and plotted using Python and Jupyter Notebook. There are 7 scripts for the different plots:

1. plotting electrolyte motion induced salt inhomogeneity (emsi.ipynb)
2. plotting capacity fade vs cycle number for different operating conditions (capacity\_fade.ipynb)
3. comparison of measured and simulated cell voltage and temperature (model\_validation.ipynb)
4. unravelling the overpotential contributions vs cycle number at 1C cycling (overpotentials.ipynb)
5. analyzing the evolution of electrolyte conductivity and diffusivity vs cycle number (plot\_electrolyte\_properties.ipynb)
6. analyzing evolution of porosity, electrolyte reservoir volume and strain during a 1C cycle (porosity\_dynamics.ipynb)
7. plotting electrolyte motion induced solid-phase lithium inhomogeneity (solid\_lithium\_concentration.ipynb)



**3. Data visualization**



Running the Python plotting scripts produces the PNG files located in "/plots".
