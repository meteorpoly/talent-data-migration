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

Talent Instance(s) with a
CDS for Apps Source Environment
CDS for Apps Target Environment
Administrative rights on both environments
Download the DataMigrationUtility from here
