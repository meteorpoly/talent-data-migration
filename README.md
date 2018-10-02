# Talent Data Transfer across Tenants
## Dynamics 365 for Talent Data Migration Utility

In this guide you will learn how to copy your Talent CDS for Apps data from a source to a target environment and even across tenants.
Following scenarios could be enabled by this tool:

- You have created great Templates, Job profiles, On-boarding Guides, On-boarding contacts, Hiring teams etc. which you would like to share across your team or organization
- You want to implement Dynamics 365 for Talent and want to give your customer a great starting point with pre-configured, maybe even industry flavored templates
- You want an automatic function during data transfer which adjusts start, end and expiry dates automatically for you 
- You have a production environment with great data and want to us it for Development, UAT (User Acceptance Tests), Payroll and Power platform integration tests
- Quick and non-production back-up and restore 

## 
![High-Level Sync Flow](https://github.com/meteorpoly/talent-data-migration/blob/master/High-level%20synch%20data%20flow.gif "High-level flow")

## Prerequisites
In order to run the below procedure you will need:

### Talent Instance(s) with a
- CDS for Apps **Source** Environment
- CDS for Apps **Target** Environment
- **Administrative** rights on **both** environments

### Setup instructions
- Download the **TalentMigration** from [here](https://github.com/meteorpoly/talent-data-migration/raw/master/TalentMigration.zip)
- Create a new folder under your **C:** drive and call it **talent-migration**
- Extract the  downloaded contents file into the newly created folder

### Data export processing steps
- Navigate to the subfolder *C:\talent-migration\ConfigurationMigration\"* and double-click on **DataMigrationUtility.exe**
- Select *Create Schema* and press **Continue** (next screen will open)
- Select *Deployment Type* **Office 365**
- Select checkbox **Display a list of available organizations**
- Login with your Source Environment admin account (eg. user@yourtenant.onmicrosoft.com)
- Select the desired Source Environment to copy from and press **Login**
- On the new screen select *File -->* **Load Schema**
- Choose one of the two templates provided in your extracted folder. **Full Load for Multi-Tenant Environments.xml** should be used if you want to export / import Talent data **across multiple Tenants** and **Full Load for Single-Tenant Environments.xml** should be used for **intra-tenant** scenarios. Both templates include most of the attract, offer and onboarding experience but **you will need to re-check and maybe adjust the data entities and fields to better fit your data needs**
- Once you are done with your adjustments click on **Save and Export** and save your configuration under a new name in the same folder. ou will be asked to export the data now so just click yes
- Click on the *...* button next to the field **Save data to file** and give your export zip a proper name --> press **Save** and then **Export Data**




