# PRO_active_growth_mixture_modeling
My internship at the WKZ 
README
This README file provides an overview of the R script used for latent class analysis among the children of the PROactive cohort using growth mixture modeling. The script performs various data processing steps, statistical analysis, and generates visualizations.
Database and Files
( "L:/Onderzoek/SP_16-707_PROactive_II/E_ResearchData/1_Students-and-researchers/2023_Jeroen_ADS-thesis_UU/01_moederbestanden-niet-analyseren/23-5-23_Database_Jeroen-Marjolein-FINAL.sav")
The database used for analysis is a SPSS file in .sav format, which can be found at the following 
Additionally, there are two additional files required for analyzing the postal codes: a .sav file and an Excel file for the conversion of postal codes to SES values.
Data Processing Steps
Combining Cantril Values: The first step involves combining the patients' Cantril values into a single row. The R script utilizes patientid_pseudo as an identifier and arranges the Cantril values in chronological order. Each row is checked to ensure that it has a Cantril value before and after the specified COVID date, which is set as 27-02-20.
Numeric Date Conversion: To ensure optimal performance and obtain correct intercepts and slope values for growth mixture modeling, the script converts the date to a numeric value representing the number of days after 01-01-2017. This conversion is later changed back to the date format, but it is crucial for accurate slope and intercept calculations in the GMM.
Data Formatting for GMM: The GMM requires the data to be in a long format. Thus, the script maintains the same identifier (id) but creates an entry for each Cantril value, associating it with the corresponding date (number of days after 01-01-2017).
Growth Mixture Modeling (GMM)
The script utilizes the lcmm package in R to perform growth mixture modeling. For detailed instructions on using the lcmm package and interpreting the results, refer to this resource:
https://www.researchgate.net/publication/340498681_Latent_Class_Growth_Analysis_and_Growth_Mixture_Modeling_using_R_A_tutorial_for_two_R-packages_and_a_comparison_with_Mplus.
The script provides various options to initialize the GMM, with the current implementation utilizing a random intercept and fixed slope. The chosen model can be analyzed using the summary() function and added to the existing data frames.
Due to the use of the Dutch language in the original data frame, certain names need to be switched. Once this is done, the script generates initial graphs to visualize the distribution of selected variables.
To track individual trajectories, the data needs to be formatted back into a long format.
Adding Socioeconomic Status (SES)
The script incorporates SES back into the analysis by utilizing the SES measurements collected closest to the COVID date (27-02-2020) from three different columns. Additionally, SES can be measured based on postal codes. In this case, non-Dutch postal codes are removed and converted using a separate file provided in the data.
Statistical Analysis and Visualization
The script includes t-testing, which requires certain assumptions to be made. After making the necessary assumptions, the script performs the t-tests.
Lastly, the script generates a variety of visualizations to represent the data.
Note: Please ensure that all required packages are installed before running the script.

