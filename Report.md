# UK Healthcare Cover Provider Analysis
## Dashboard Summary
This dashboard provides insight into the Healthcare coverage providers in the UK. It covers various metrics such as the departments that took the most patients to treat, the diagnosis doctors came up with and the type of referral they had upon the visit. It also highlights the country-wise comparison and proportion of the amount that went into each procedure. Furthermore, the analysis can be broken down to the sex of the patient, cover provider, room type, age of patients and diagnosis. The dashboard indicated a total revenue generation of 2.81 million GBP whereas, 567,000 GBP in the medication cost. The total amount that was spent on the billing of room charges is 35,000 GBP.
## Data Preparation and Modelling
The data was imported into Power Query from a CSV file for cleaning and sorting, which was necessary before evaluating the dataset.
### Data Modeling
The data model includes a table imported into Power BI along with a measure table. A measure table serves as a structured and efficient way to store all our measures in one place. The following illustration displays the data model.
#
![model](https://github.com/user-attachments/assets/d8071ef2-116d-4fa2-9ee0-08f9c63dfb77)
### Measure Table
A measure table is a proactive approach to keeping your work organized and orderly. For the analysis, the measure table contains all the DAX expressions needed to assess the KPIs for the dashboard. The following DAX expressions are used for analysing this dashboard:
**Total Billing Amount:** Accumulative of all the billing metrics including and excluding the insurance cover.
```
Total billing amount = 
[Total Insurance Covered] + [Total room charges] + [Total Medication Cost]
```
**Total Insurance Covered:** Amount covered by insurance companies is given by the following expression:
```
Total Insurance Covered = SUM(visits[Insurance Coverage])
```
**Uninsured Revenue:** Revenue from uninsured patients.
```
Revenue from no insurance cover = [Total billing amount] - [Total Insurance Covered]
```
**Medication Cost:** Billing from medication cost
```
Total Medication Cost = SUM(visits[Medication Cost])
```
**Room Charges:** Total room charges that were billed inclusive or exclusive of the insurance cover
```
Total room charges = SUMX(visits,
visits[Room Charges(daily rate)] * visits[Length of stay])
```
## Dashboard Overview:
This dashboard covers wide arrays of insights. It can be observed that Edinburgh is the city with the highest billing amount while on the contrary, Wales turns out to be the most billed country. It is illustrated that cardiology is the most billed department whereas, people come to the hospital for emergency services most of the time. Patients were diagnosed with appendicitis most of the time and X-ray is the most billed procedure done in the hospital. In-depth analysis can be done by using the filter by breaking down each metric on the basis of age of the patient, cover provider, room type, service type and diagnosis.

![dash](https://github.com/user-attachments/assets/be5d629d-bfbf-4e06-bbbe-c930944ef111)
![filter](https://github.com/user-attachments/assets/fc9e4a6f-b613-4d99-a83c-7f9ed9fe531b)
