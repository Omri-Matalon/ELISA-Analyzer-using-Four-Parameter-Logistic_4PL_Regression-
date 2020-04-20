# ELISA-Analyzer-using-Four-Parameter-Logistic_4PL_Regression

## **Introduction**
The enzyme-linked immunosorbent assay (ELISA) is quantitative method for measuring the concentration of biological soluble factors in liquid samples, commonly used in research, biotechnology and medical laboratories. 
The method involves loading liquid samples in plate wells that specifically bind a target factor (usually a protein), followed by adding a colorimetric compound that produces a detectable signal, which is proportional to the concentration of the target protein. 
To render the method quantitative (i.e. allowing determine the exact concentration of proteins in the test samples), a standard curve is used in each assay. The standard curve consist of a serial diluted samples that contain known concentrations of the target protein. The Optical Density (OD; the measured color intensity) and the know concentrations are used for building a standard-curve (std curve) of OD signal as a function of sample concentration. This standard curve is then used to interpolate the concentration of the tested samples. 

Due to the nature of biological reactions and the method used for measuring the OD, which have lower sensitivity at higher protein concentrations, a **4 Parameter Logistic (4PL) model** is used for generating the standard curves, to accurately determining the concentration in the test samples. 

## **ELISA Analyzer Description** 
ELISA results in research laboratories are usually analyzed manually, which is a time consuming and error prone procedure. In the current project, an automatic ELISA analyzer was established to improve the accuracy and reproducibility of ELISA results. 

**In general, ELISA analysis involves the following steps (which are implemented in the attached program):** 

1. Loading the OD values of the tested and standard curve samples.
2. Subtracting OD values of Blank negative controls (samples without any protein that represent the background signal). 
3. Constructing the Standard Curve by a 4PL model of OD as a function of protein concentrations.
4. Calculating the concentration of tested samples using the standard curve. 
5. Exporting the calculated concentrations of the tested samples into Excel file report.  

Please note, samples with OD values that falls outside the signal range of the standard curve are excluded from the analysis due to inability to accurately determine their concentration. These samples are labeled as below lower-limit-of-quantification (LLOQ) or above upper-limit-of-quantification (ULOQ). Samples with high protein concentration are diluted before the assay, and the dilution factor is being considered in the analysis to calculate the samples' actual concentrations.    

## **ELISA Analyzer inputs**  
The ELISA analyzer takes as an **input an Excel file ("ELISA Tamplet.xlsx")**, in which each work sheet represent a different ELISA plate (usually more than one plate is ran in each experiment). In each work sheet, the user need to copy and paste sample OD values (into "sample ODs" table), the dilution factor of each sample (into "Sample dilution factors" table) and standard curve OD values (into "Standard curve OD" table).

**When running the program, the user will be asked to enter the following:** 
1. Entre the file name (press Enter for using the default "ELISA Tamplet.xlsx" name).
2. How many plates would you like to analyze? (press Enter for default value of 3).
3. Enter the highest std curve point (press enter for using the default value of 1600 pg/ml)
4. Enter the dilution factor of standard curve (press Enter for default value of 2).
 
## **ELISA Analyzer output**
**The program will create an Excel report with the following sheets:**
1. Calculated concentrations: samples' calculated concentrations  
2. Errors (ODs outside std range): indicating samples with OD signal below LLOQ or above ULOQ.
3. Concentration without (w_o ) errors: sample concentration, excluding samples below LLOQ or above ULOQ.
4. Sample OD - raw data
5. Sample OD minus blank: after subtracting background signal.
6. Sample dilution factors.
7. Std curve details: including model parameter values, goodness of fit (R^2), and standard curve images.    

## **Files include in the current repository** 
1. ReadMe file.
2. Program Jupyter notebook.
3. "ELISA Tamplet.xlsx " file (including example OD values for 3 plates).
4.  Example "ELISA_4PL_Analysis_Report.xlsx" output file.

