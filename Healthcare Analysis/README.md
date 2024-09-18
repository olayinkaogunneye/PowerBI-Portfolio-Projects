## Hospital Inpatient Discharges - Total Hip Replacement (New York State)


### Overview
This dataset contains information on hospital inpatient discharges for total hip replacement surgeries in New York State. The data includes various patient demographics, hospital facility details, admission types, medical procedure codes, and costs associated with these procedures. It provides valuable insights into healthcare delivery and outcomes for total hip replacement procedures across hospitals in New York.

Data Source
Dataset: Hospital Inpatient Discharges for Total Hip Replacement (New York State)

Entries: 26,594 rows

Attributes: 30 columns

Location: New York State, USA



### Data Dictionary

Below is a brief description of the key columns:

| Column Name                          | Description                                                                 |
| ------------------------------------- | --------------------------------------------------------------------------- |
| `health_service_area`                 | Health service area of the hospital in New York State                        |
| `hospital_county`                     | County in New York where the hospital is located                             |
| `operating_certificate_number`        | Operating certificate number of the hospital                                 |
| `facility_id`                         | Unique ID for the hospital facility                                          |
| `facility_name`                       | Name of the hospital                                                        |
| `age_group`                           | Age group of the patient (e.g., 0 to 17, 50 to 69)                           |
| `zip_code_3_digits`                   | First three digits of the patient's zip code                                 |
| `gender`                              | Gender of the patient (M/F)                                                  |
| `race`                                | Race of the patient                                                          |
| `ethnicity`                           | Ethnicity of the patient (e.g., Hispanic or Latino)                          |
| `length_of_stay`                      | Length of the hospital stay (in days)                                        |
| `type_of_admission`                   | Type of hospital admission (e.g., elective, emergency)                       |
| `patient_disposition`                 | Patient's discharge status (e.g., discharged to home)                        |
| `discharge_year`                      | Year of discharge                                                           |
| `ccs_diagnosis_code`                  | Clinical Classification Software (CCS) diagnosis code                        |
| `ccs_diagnosis_description`           | Description of the diagnosis                                                 |
| `ccs_procedure_code`                  | CCS procedure code associated with the treatment                             |
| `ccs_procedure_description`           | Description of the procedure performed                                       |
| `apr_drg_code`                        | All Patient Refined Diagnosis Related Group (APR-DRG) code                   |
| `apr_drg_description`                 | Description of the APR-DRG category                                          |
| `apr_mdc_code`                        | Major Diagnostic Category (MDC) code                                         |
| `apr_mdc_description`                 | Description of the MDC                                                      |
| `apr_severity_of_illness_code`        | Code indicating the severity of the illness                                  |
| `apr_severity_of_illness_description` | Description of the severity (minor, moderate, major, extreme)                |
| `apr_risk_of_mortality`               | Risk of mortality (minor, moderate, major, extreme)                          |
| `apr_medical_surgical_description`    | Whether the case is surgical or medical                                      |
| `attending_provider_license_number`   | License number of the attending provider                                     |
| `operating_provider_license_number`   | License number of the operating provider                                     |
| `total_charges`                       | Total charges for the treatment ($)                                          |
| `total_costs`                         | Total costs for the hospital ($)                                             |



#### Usage
This dataset can be used for:

Analyzing healthcare costs and outcomes for hip replacement surgeries in New York State.

Investigating variations in treatment across different counties or demographics.

Understanding the relationships between patient characteristics (age, race, etc.) and discharge outcomes.
