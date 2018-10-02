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

## How does the Configuration Migration tool work?
The following diagram illustrates how the Configuration Migration tool is used for migrating configuration data.

![Config Manager](https://docs.microsoft.com/en-gb/dynamics365/customer-engagement/admin/media/config-migration-process-flow.png "Configuration Manager")

**Step 1**: Define the schema of the source data to be exported: The schema file (.xml) contains information about the data that you want to export such as the entities, attributes, relationships, definition of uniqueness of the data, and whether the plug-ins should be disabled before exporting the data. More information: Create a schema to export configuration data

**Step 2**: Use the schema to export data: Use the schema file to export the data into a .zip file that contains the data and the schema of the exported data. More information: Create a schema to export configuration data

**Step 3**: Import the exported data: Use the exported data (.zip file) to import into the target Dynamics 365 instance. The data import is done in multiple passes to first import the foundation data while queuing up the dependent data, and then import the dependent data in the subsequent passes to handle any data dependencies or linkages. This ensures clean data import. More information: Import configuration data

### More details can be found here
https://docs.microsoft.com/en-gb/dynamics365/customer-engagement/admin/manage-configuration-data#how-does-the-configuration-migration-tool-work

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
- Login with your **Source** Environment admin account (eg. user@yourtenant.onmicrosoft.com)
- Select the desired **Source** Environment to copy from and press **Login**
- On the new screen select *File -->* **Load Schema**
- Choose one of the two templates provided in your extracted folder. **Full Load for Multi-Tenant Environments.xml** should be used if you want to export / import Talent data **across multiple Tenants** and **Full Load for Single-Tenant Environments.xml** should be used for **intra-tenant** scenarios. Both templates include most of the attract, offer and onboarding experience but **you will need to re-check and maybe adjust the data entities and fields to better fit your data needs**
- Once you are done with adjustments click on **Save and Export** and save your configuration under a new name in the same folder. You will be asked to export the data now so just click **Yes**
- Click on the *...* button next to the field **Save data to file** and give your export zip a proper name --> press **Save** and then **Export Data**. You should dialogs similar to:

![Export start](https://github.com/meteorpoly/talent-data-migration/blob/master/Screen%202.gif "High-level flow")
![Export end](https://github.com/meteorpoly/talent-data-migration/blob/master/Screen%204.gif "High-level flow")

### Data import processing steps
- Navigate to the subfolder *C:\talent-migration\ConfigurationMigration\"* and double-click on **DataMigrationUtility.exe**
- Select *Import Data* and press **Continue** (next screen will open)
- Select *Deployment Type* **Office 365**
- Select *Deployment Type* **Office 365**
- Select checkbox **Display a list of available organizations**
- Login with your **Target** Environment admin account (eg. user@yourtenant.onmicrosoft.com)
- Select the desired **Target** Environment to import into and press **Login**
- On the new screen click on the *...* button next to the field *Zip File -->* and select the previously exported source zip file
- Click **Import Data** and wait until the process is finsished (it might run more than 10 minutes, depending on volume of course)

### Validate your import
Open the Target Talent App (and Environment) at https://attract.talent.dynamics.com/jobs and check if all data is present. 

### Important steps to enable cross tenant  imports
In case you don't see the data you will need to open the Worker entity in Excel and adjust the Worker's:
- *Office Graph Identifier* - can be retrieved via the Office Graph Explorer https://developer.microsoft.com/en-us/graph/graph-explorer 
- *Primary Email Address* - The Target Environment Talent User's mail
- *User (Lookup)* - The Target Environment Talent User Object (will be selectable on the right task pane in excel)

Enjoy!

### License
The MIT License (MIT)

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
