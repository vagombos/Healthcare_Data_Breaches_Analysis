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
The ["breach.csv"](data/breach_report.csv) data download from the U.S. HHS site was imported into Python with the pandas and numpy libraries. Rows with null values were dropped, and further transformations for particular analyses/visualizations included filtering data for "Hacking/IT Incidents", splitting the data into train/test sets (for predictive models), aggregating counts by month and year, and text-to-column creation of new columns from the contents of a single column with multiple possible categories ("location_of_breached_information"). Because one column ('web_description') was mostly null, it was also excluded from the dataframe. The complete cleaned up dataframe resulted in 900 rows. The full code for these transformations and analyses can be found in the Jupyter Notebook file on this site's data folder ["US_HSS_SecurityBreachAnalysis"](data/US_HSS_SecurityBreachAnalysis.ipynb).  

#### Initial Summaries and Overview  
  * Preview (head function) of first lines of data within this dataframe indicates the fields and the type of content that might be of interest:  

```html
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>name_of_covered_entity</th>
      <th>state</th>
      <th>covered_entity_type</th>
      <th>individuals_affected</th>
      <th>breach_submission_date</th>
      <th>type_of_breach</th>
      <th>location_of_breached_information</th>
      <th>business_associate_present</th>
      <th>Email</th>
      <th>Network Server</th>
      <th>Other</th>
      <th>Paper/Films</th>
      <th>Desktop Computer</th>
      <th>Electronic Medical Record</th>
      <th>Laptop</th>
      <th>Other Portable Electronic Device</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>iTrust Wellness Group</td>
      <td>SC</td>
      <td>Healthcare Provider</td>
      <td>981</td>
      <td>8/10/2023</td>
      <td>Hacking/IT Incident</td>
      <td>Email</td>
      <td>No</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Madera County</td>
      <td>CA</td>
      <td>Health Plan</td>
      <td>1146</td>
      <td>8/9/2023</td>
      <td>Unauthorized Access/Disclosure</td>
      <td>Email</td>
      <td>No</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>PCC Pediatric EHR Solutions</td>
      <td>VT</td>
      <td>Business Associate</td>
      <td>520</td>
      <td>8/9/2023</td>
      <td>Unauthorized Access/Disclosure</td>
      <td>Email</td>
      <td>Yes</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Premera Blue Cross</td>
      <td>WA</td>
      <td>Health Plan</td>
      <td>33212</td>
      <td>8/8/2023</td>
      <td>Hacking/IT Incident</td>
      <td>Network Server</td>
      <td>Yes</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Redwood Coast Regional Center</td>
      <td>CA</td>
      <td>Healthcare Provider</td>
      <td>1345</td>
      <td>8/7/2023</td>
      <td>Hacking/IT Incident</td>
      <td>Email</td>
      <td>No</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
```
 

  * A summary of the top ten states by count and % of breaches for the entire time period (note that bottom two were tied):
    
 ![Top 10 States](images/Top10States.PNG)  


---
### References 
[^1]: Brodkin, J. (2023, August 4). Our health care system may soon receive a much-needed cybersecurity boost. Ars Technica. Retrieved from https://arstechnica.com/information-technology/2023/08/our-health-care-system-may-soon-receive-a-much-needed-cybersecurity-boost/
