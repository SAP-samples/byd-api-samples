# SAP Business ByDesign - API Usage Samples

## Description

This repository provides example Postman collections consuming SAP Business ByDesign APIs and can be used to get insights how to integrate and extend SAP Business ByDesign.

[SAP Business ByDesign](https://www.sap.com/products/business-bydesign.html) is a cloud ERP solution for small and mid-market companies. 
SAP Business ByDesign (ByD) is designed as open business process platform and provides a comprehensive portfolio of APIs and integration capabilities.  
The sample Postman collections illustrate hands-on how to access master data, business documents and analytical data in context of ByD business processes with a focus on ByD OData APIs.

The repository is structured in API sample packages. 
Each package contains Postman collections, a Postman environment and all ByD Custom OData Services required to run the OData requests of the Postman collection.

The following API sample packages are available:
- **Analytics**: Access ByD built-in analytics incl. reports and data sources
- **Business Partner Data**: Create and read account, supplier and business partner data
- **End-to-End Scenarios**: Run ByD business processes using APIs to get insights how to create, change and read involved business documents and how to create business document relationships to achieve a meaningful document flow
	- Lead to Opportunity to Quote
	- Selling Services
	- Field Service and Repair
	- Procure to Stock
	- Sell from Stock
	- Drop Shipment
	- Make to Stock
	- Pay Due Items using Bank Statements
- **Product and Service Portfolio**: Create, change and read price lists and discount lists
- **Product Data**: Create, change and read materials and service products
- **Projects**: Create, change and read cost collecting projects and customer projects 
	- Cost collection project with task hierarchy
	- Cost collecting project with project team and work
	- Customer project with planning data
	- Sell project-based services (sales order > project > project time recordings)
- **Sales Orders**: Create, change and sales orders; contains examples to use business object attachments as well

Please check the description of the respective Postman collection for more information.

## Requirements

Users must be familiar with SAP Business ByDesign, and with Postman.
- [SAP Business ByDesign Help Portal](https://help.sap.com/viewer/product/SAP_BUSINESS_BYDESIGN/)
- [Postman Learning Center](https://learning.getpostman.com/)
    
Users must have an SAP Business ByDesign license.  *This is a paid product, no trial version is available at this time.*

## Download and Installation

1. Install [Postman API Development Environment](https://www.getpostman.com/)
2. Download the example ByD Custom OData Services, Postman collections and Postman environments from GitHub as [zip-file](https://github.com/SAP/sapbydesign-api-samples/archive/master.zip)

## Configuration

All sample Postman collections are tailored to run on SAP Business ByDesign Partner Demo Tenants (reference systems) with preconfigured and loaded sample data provided by SAP.  
Nevertheless you can use the Postman collections and sample Custom OData Services in other ByD systems as well, if you adopt Postman environment variables and Postman requests according the business configuration and master data of your ByD system.

All configuration settings described below are based SAP Business ByDesign reference systems with preconfigured and loaded sample data provided by SAP.

Configuration steps:
1. Open SAP ByDesign work center view "*Application and User Management - OData Services*" and upload the Custom OData Services in sub-folder "*Custom OData Service*".
2. Open the desktop app *Postman* and import the Postman collections and Postman environments in sub-folder "*Postman Collection*".
3. Check the configuration description of the respective API sample package below for package specific setup instructions.
4. Select the Postman environment and maintain the variables 
	- *TenantHostname* (for example *my123456.sapbydesign.com*) 
	- *User* and *Password* (enter a business user with access to all work center views listed in the API sample package description below)
	- *CommunicationUser* and *CommunicationUserPW* (enter the communication user used for the communication arrangements created as described in the API sample package description below)
5. Run the Postman requests within a Postman collection folder in the listed order.

API sample package specific configurations:

#### Analytics 

OData API for reports: Assign the following work center views to your SAP ByDesign business user to be able to access the reports used in the OData request samples:
- *Customer Invoicing - Invoice Documents*
- *Personnel Administration - Employees*
- *Inbound Logistics - By Warehouse Request*
- *Purchase Requests and Orders - Purchase Orders*
- *General Ledger - Journal Entries*
- *Business Partner Data - Accounts*
- *Application and User Management - Business Users*
- *Sales Orders - Sales Orders*
- *Receivables - Customer Accounts*

OData API for data sources: Create a communication user and expose data sources used by the sample OData requests: 
1. Enable the OData API for Data Sources in your ByD Business Configuration: *Built-in Services and Support* >> *System Management* >> *Analytics* >> *Do you want to enable analytical OData services for data sources?*
2. Create a communication user to access the OData service: Create a Communication Arrangement for Communication Scenario *Analytics Data Sources ODATA* and maintain the technical user
3. Expose the following data sources in work center view *Business Analytics - Data Sources*:
	- *Sales Order Header* (Crmslohb)
	- *Sales Order Item* (Crmsloib)
	- *Material General data* (MatGeneral)
	- *Stock Overview* (Scminvv02)
	- *G/L Account Items* (Finglau02)
	- *Company Master Data* (/mom/company)

You may need to clear cookies stored in Postman to retrigger authentication using the correct SAP ByDesign user.

#### Business Partner Data

Required business user authorizations (ByD Work Center Views):
- *Business Partner Data - Business Partners*
- *Business Partner Data - Accounts*
- *Business Partner Data - Suppliers*

Configure additional Web Service APIs used in the Postman collection:
1. Work center view *Application and User Management - Communication Systems*: Create a communication system representing the remote system
2. Work center view *Application and User Management - Communication Scenarios*: Create a communication scenario with the following web service APIs:
	- *Manage Business Partners*
	- *Query Business Partners*
	- *Manage Accounts*
	- *Query Accounts*
	- *Manage Suppliers*
	- *Query Suppliers*
3. Work center view *Application and User Management - Communication Arrangements*: Create a communication arrangement using the communication scenario and communication system and enter the credentials

#### End-to-End Scenarios

Required business user authorizations (ByD Work Center Views):
- *Marketing - Leads*
- *New Business - Opportunity List*
- *New Business - Sales Quotes*
- *Sales Orders - Sales Orders*
- *Customer Invoicing - Invoice Requests*
- *Customer Invoicing - Invoice Documents*
- *Service Desk - Service Requests*
- *Service Orders - Service Order Processing*
- *Field Service and Repair - Service Confirmations*
- *Purchase Requests and Orders - Purchase Orders*
- *Inbound Logistics - Purchase Orders*
- *Inbound Logistics - Inbound Delivery Notifications*
- *Inbound Logistics - Inbound Deliveries*
- *Supplier Invoicing - Invoices and Credit Memos* (Supplier invoices can only be posted if the user is authorized to post supplier invoices and if supplier invoices do not require approvals. Otherwise supplier invoices remain in status "ready for posting")
- *Outbound Logistics - Delivery Proposals*
- *Outbound Logistics - Outbound Deliveries*
- *Supply Control - Process Production Proposals*
- *Production Control - Production Orders*
- *Execution - Production Tasks*
- *Receivables - Customer Accounts*
- *Liquidity Management - My Banks*
- *Liquidity Management - Inbound Files*
- *Liquidity Management - Bank Statements*

Assign your user (employee or service agent) to the organizational unit *A1100* and job *System Administrator* to ensure proper defaulting based on your organizational assignment.

Configure the determination methode for external references:  
ByD work center *Business Configuration*: Open the fine tuning activity *External Reference Number Determination for Customer Invoice* and set the determination method to *Copied from Predecessor Reference ID*.

Deactivate approval for service confirmations:  
ByD work center *Business Configuration*: Open your project scope and deactivate the scoping question: *Service* > *Service and Repair* > *Service Confirmation* > *Do you want to use an approval process for service confirmations?*

Configure bank statement processing:  
The bank statements created by this scenario are automatically allocated if you apply the following business configuration in your ByD system:
1. Fine-Tuning activity *Automatically Generated Bank Statements* > *Assign import formats for bank statements*:  
Add row using the values: *Company ID: 1000* | *Bank ID: 1000002* | *Bank Statement Format: 02 - BAI2 US*
2. Fine-Tuning activity *Settings for Posting Automatically Generated Bank Statements*:  
Add row using the values: *Seq.: 1* | *Company: 1000* | *Bank Country: \** | *Bank ID: \** | *Currency: \** | *Bank Account ID: \** | *Manual Post Necessary: False*
3. Fine-Tuning activity *Global Settings for Payment* > *Create and edit rules for analyzing memo lines*:  
Add 4 rows using the following values:
	- Rule 1: *Description: Customer* | *Rule Type: 4* | *Rule Definition Mode: Expert* | *Regular Expression: (ORIG CO NAME\=).\**
	- Rule 2: *Description: AR External Reference (w seconds)* | *Rule Type: 13* | *Rule Definition Mode: Expert | Regular Expression: (\R\-\d{4}\d{1,2}\d{1,2}\d{2}\d{2}\d{2})*
	- Rule 3: *Description: AR External Reference 1INV* | *Rule Type: 13* | *Rule Definition Mode: Expert* | *Regular Expression: (1INV-\d{1,}\-\d{1,})*
	- Rule 4: *Description: AR External Reference (w/o seconds)* | *Rule Type: 13* | *Rule Definition Mode: Expert* | *Regular Expression: (\R\-\d{4}\d{1,2}\d{1,2}\d{2}\d{2})*

Create company payment file register:  
Open work center view *Liquidity Management - Inbound Files*, click on *New* > *Inbound File* and enter the following values:  
	*Type: Bank Statement* | *Company: 1000* | *Bank ID: 1000002* | *Import Format: BAI2 US*.  
Save without adding an attachment.  
The system created a company payment file register for company 1000 that can now be used for file uploads via OData.

Configure additional Web Service APIs used in the Postman collection:
1. Work center view *Application and User Management - Communication Systems*: Create a communication system representing the remote system
2. Work center view *Application and User Management - Communication Scenarios*: Create a communication scenario with the following web service APIs:
	- *Query Service Confirmations*
	- *Manage Service Confirmations*
	- *Manage Production Proposals*
	- *Query Production Orders*
	- *Query Production Lots*
	- *Manage Production Lots*
3. Work center view *Application and User Management - Communication Arrangements*: Create a communication arrangement using the communication scenario and communication system and enter the credentials

Remarks:
- You can use the Postman collection folder *Procure to Stock* to fill up your stock before running the process *Sell from Stock* to avoid any failure of availability-to-promise checks.
- The Postman collection folder *Pay Due Items using Bank Statements* clears due items originating from customer invoices created by all other folders in this collection.

#### Product and Service Portfolio

Required business user authorizations (ByD Work Center Views):
- *Product and Service Portfolio - Pricing*
- *Product and Service Portfolio - Pricing (Gross)*

Configure additional Web Service APIs used in the Postman collection:
1. Work center view *Application and User Management - Communication Systems*: Create a communication system representing the remote system
2. Work center view *Application and User Management - Communication Scenarios*: Create a communication scenario with the following web service APIs:
	- *Manage Price Lists*
	- *Query Price Lists*
3. Work center view *Application and User Management - Communication Arrangements*: Create a communication arrangement using the communication scenario and communication system and enter the credentials

#### Product Data

Required business user authorizations (ByD Work Center Views):
- *Product Data - Materials*
- *Product Data - Services*

#### Projects

Required business user authorizations (ByD Work Center Views):
- *Project Management - Projects*
- *Sales Orders - Sales Orders*
- *Time Administration - Employees*
- *Time Administration - Time Sheet*

Assign your user (employee or service agent) to the organizational unit *A1100* and job *System Administrator* to ensure proper defaulting based on your organizational assignment.

#### Sales Orders

Required business user authorizations (ByD Work Center Views):
- *Sales Orders - Sales Orders*

Assign your user (employee or service agent) to the organizational unit *A1100* and job *System Administrator* to ensure proper defaulting based on your organizational assignment.

## How to obtain support

This repository is provided "as-is"; no support is available.

## License

Copyright (c) 2019 SAP SE or an SAP affiliate company. All rights reserved.
This file is licensed under the SAP Sample Code License except as noted otherwise in the [LICENSE](/LICENSE.txt) file.

