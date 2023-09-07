<a id="healthcare-data-breaches-analysis"></a>
# Analysis of Healthcare Data Breaches 
### Case Study Using US Dept. of Health and Human Services (USHHS) Open Source Data from July 19, 2021 to August 10, 2023  
##### - [Statement of Business Task](#statement-of-business-task)
##### - [Description of Data Source](#description-of-data-source)
##### - [Data ETL Analyses and Results](#data-etl-analyses-and-results)
##### - [Conclusions and Insights](#conclusions-and-insights)
##### - [References](#references)
---
### Statement of Business Task
Cybersecurity is important across domains, but the U.S. healthcare industry is particularly vulnerable, with many cybercriminal attacks in the last decade trying to take advantage of medical facilities' high stakes data for extortion.[^1] The current business task is to conduct an exploratory analysis, to find patterns and potential avenues for further inquiry, into one element of cybersecurity risk that criminals may take advantage of: breaches of unsecured protected health information.  

### Description of Data Source
This open public data source is provided by the U.S. Department of Health and Human Services (HHS) in accordance with section 13402(e)(4) of the HITECH Act (https://ocrportal.hhs.gov/ocr/breach/breach_report.jsf).
The data range selected included cases currently under investigation, from July 19, 2021 to August 10, 2023.  

### Data ETL Analyses and Results
The ["breach.csv"](data/breach_report.csv) data download from the U.S. HHS site was imported into Python with the pandas and numpy libraries. Rows with null values were dropped, and further transformations for particular analyses/visualizations included filtering data for "Hacking/IT Incidents", splitting the data into train/test sets (for predictive models), aggregating counts by month and year, and text-to-column creation of new columns from the contents of a single column with multiple possible categories ("location_of_breached_information"). The full code for these transformations and analyses can be found in the Jupyter Notebook file on this site's data folder ["US_HSS_SecurityBreachAnalysis"](data/US_HSS_SecurityBreachAnalysis.ipynb).  

#### Initial Summaries and Overview  
  * Preview (head function) of first lines of data within this dataframe indicates the fields and the type of content that might be of interest:

name_of_covered_entity	state	covered_entity_type	individuals_affected	breach_submission_date	type_of_breach	location_of_breached_information	business_associate_present	web_description
```
0	iTrust Wellness Group	SC	Healthcare Provider	981	8/10/2023	Hacking/IT Incident	Email	No	NaN
1	Madera County	CA	Health Plan	1146	8/9/2023	Unauthorized Access/Disclosure	Email	No	NaN
2	PCC Pediatric EHR Solutions	VT	Business Associate	520	8/9/2023	Unauthorized Access/Disclosure	Email	Yes	NaN
3	Premera Blue Cross	WA	Health Plan	33212	8/8/2023	Hacking/IT Incident	Network Server	Yes	NaN
4	Redwood Coast Regional Center	CA	Healthcare Provider	1345	8/7/2023	Hacking/IT Incident	Email	No	NaN```  

---
### References 
[^1]: Brodkin, J. (2023, August 4). Our health care system may soon receive a much-needed cybersecurity boost. Ars Technica. Retrieved from https://arstechnica.com/information-technology/2023/08/our-health-care-system-may-soon-receive-a-much-needed-cybersecurity-boost/
