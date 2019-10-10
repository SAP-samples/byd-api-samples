# SAP Business ByDesign - API Samples

## Description

This repository provides Postman collections with example SAP Business ByDesign web service requests and can be used to get insights how to integrate and extend SAP Business ByDesign.

[SAP Business ByDesign](https://www.sap.com/products/business-bydesign.html) is a cloud ERP solution for small and mid-market companies. 
SAP Business ByDesign (ByD) is designed as open business process platform and provides a comprehensive portfolio of APIs and integration capabilities. You find an overview of all ByD APIs in the SAP Community blog post [SAP Business ByDesign - API Overview](https://blogs.sap.com/2019/09/26/sap-business-bydesign-an-api-overview/). 
The Postman collections of this repository illustrate hands-on how to access master data, business documents and analytical data in context of ByD business processes with a focus on ByD OData APIs.

The repository is structured in API sample packages. 
Each package contains Postman collections, a Postman environment and ByD Custom OData Services required to run the OData requests of the Postman collections.
You find the sample ByD Custom OData Services in folder "Custom OData Services" and the Postman collections and environments in folder "Postman". Postman collections and environments that belong together have the same name. The ByD Custom OData Services are used by multiple Postman collections; you find a list of required ByD Custom OData Services in the description of each Postman collection.

This repository contains the following API sample packages:
- **Analytics**: Access ByD built-in analytics incl. reports and data sources
- **Master Data**: Access ByD master data objects using APIs 
	- Organizational Structure
	- Material
	- Service Product
	- Sales Price
	- Business Partner
	- Customer
	- Supplier
	- Employee and Position
	- Code lists
- **Reference Scenarios**: Run ByD business processes using APIs to get insights how to create, change and read involved business documents and how to create business document relationships to achieve a meaningful document flow
	- Lead to opportunity to quote
	- Order to cash for services
	- Procure to pay for services
	- Field service and repair
	- Procure to stock
	- Sell from stock
	- Drop shipment
	- Make to stock
	- Clear due items using bank statements
- **Projects**: Create, change and read cost collecting projects and customer projects 
	- Cost collection project with task hierarchy
	- Cost collecting project with project team and work
	- Customer project with planning data
	- Sell project-based services (sales order > project > project time recordings)
- **Sales and Commerce Scenarios**: Run ByD sales and commerce processes using APIs to get insights how to create, change and read involved business documents and how to create business document relationships to achieve a meaningful document flow. 
	- Sell from stock with external payment
	- Create customer invoices with external payment
	- Customer return to stock
	- Pre-confirm payments using clearing house statements
	- Confirm payments using bank statements
	- Create sales orders using a nested create, batch and node-by-node
	- Create sales orders with attachments
	- Create sales orders with externally provided prices, discounts and surcharges

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

All sample Postman collections are tailored to run on **SAP Business ByDesign Partner Demo Tenants** (reference systems) with preconfigured and loaded sample data provided by SAP.  
Nevertheless you can use the Postman collections and sample Custom OData Services in other ByD systems as well, if you adopt Postman environment variables and Postman requests according the business configuration and master data of your ByD system.

Steps to setup and run the API sample requests:
1. **SAP Business ByDesign:** Open ByD work center view "*Application and User Management - OData Services*" and upload the Custom OData Services in folder "*Sample OData Services*".
2. **Postman:** Open the desktop app *Postman* and import the Postman collections and Postman environments in folder "*Postman*". As result you should have a number of collections and environments uploaded to Postman. The environments contain test data and system access information. The collections contain multiple folders and sub-folders, each with a sequence of web service requests and scripts that run before and after the web service request. Each environment belongs to a collection (you can easily identify the collections and environments that belong together by their names).
3. **SAP Business ByDesign:** Check the ByD business configuration and configure ByD web services. Check the descriptions of the Postman collections and follow the instructions of the respective Postman collection.
4. **Postman:** Open the Postman environment and maintain the variables 
	- *TenantHostname* (for example *my123456.sapbydesign.com*) 
	- *User* and *Password* (enter a business user with access to all work center views listed in the description of the Postman collection)
	- *CommunicationUser* and *CommunicationUserPW* (enter the communication user used for the communication arrangements created as described in the description of the Postman collection)
5. **Postman:** Open the Postman Runner. The runner is used to automatically run a sequence of OData requests. 
6. **Postman Runner:** 
	1. Select the collection and the folder
	2. Select the environment 
	3. Select the check boxes “Keep variable values” and “Run collection without using stored cookies”
	4. Click on “Run …” 
		- Make sure you always choose collections and environments that belong together – otherwise it does not work!
		- In the protocol you find IDs and valuations that you can use to find the corresponding objects in the ByD UI
7. **Postman:** Alternatively you can run the OData requests manually as well: 
	1. Open the Postman collection folder
	2. Select the Postman environment (Make sure you always choose collections and environments that belong together)
	3. Select the request and click “Send”
	4. Select the next request and click “Send” 
	5. … (always keep the order of the OData requests and do not skip any OData request)

## How to obtain support

This repository is provided "as-is"; no support is available.

## License

Copyright (c) 2019 SAP SE or an SAP affiliate company. All rights reserved.
This file is licensed under the SAP Sample Code License except as noted otherwise in the [LICENSE](/LICENSE.txt) file.

