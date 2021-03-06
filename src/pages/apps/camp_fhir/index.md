---
path: "/apps/camp-fhir"
title: "CAMP FHIR"
seo:
    title: "CAMP FHIR"
    keywords: ""
    description: ""
---
## CAMP FHIR

## Overview

CAMP FHIR (Clinical Asset Mapping Program for FHIR) is a custom software application that was developed by Green Team, in collaboration with Orange Team, as part of the Translator project in an effort to facilitate the sharing of clinical data across the Translator Consortium.

**Motivation**

While clinical data are central to the Translator program, Translator teams have not adopted a uniform clinical data model (CDM) to enable the sharing of clinical data across the consortium. Moreover, even if current Translator teams were to adopt a uniform CDM, future Translator collaborators and users may not be positioned to support the agreed-upon model.

The challenge of cross-institutional data sharing is by no means limited to the Translator program. Institutions who wish to participate in a multi-institutional collaboration may not support the same CDM. For instance, one institution may use i2b2, whereas another one uses OMOP. In these situations, the institution without the adopted CDM simply not be able to stand up a new CDM to accommodate the other institution. Indeed, mapping institutional electronic health record (EHR) data to any one of the major CDMs is resource- and personnel-intensive, and it requires an ongoing commitment to maintain and refresh infrastructure and data over time. 

**Approach**

To overcome these challenge, we adopted the Health Level Seven International Fast Healthcare Interoperability Resources (FHIR) as a “meta-CDM” or single standard to represent clinical data. CAMP FHIR efficiently transforms clinical data to FHIR irrespective of CDM, thus providing source-agnostic CDM-to-FHIR mapping.

Mapping with CAMP FHIR involves: (1) mapping each source variable to its corresponding FHIR element; and (2) mapping each item in the source data’s value sets to the corresponding FHIR value set item, for variables with strict value sets.

![**CAMP FHIR Overview**](CAMP_FHIR.png)

**Use Cases**
To date, CAMP FHIR has been used to transform data from the i2b2 and PCORnet CDMs, although it is designed to allow input from any source CDM (Pfaff et al. 2019).

In our initial use case, we have used CAMP FHIR to transform i2b2 data on patients with an asthma-like condition for subsequent integration with environmental exposures data using a second custom sofwate pipeline, FHIR PIT (FHIR Patient data Integration Tool). Data quality and integrity were validated against the origin point of the data, our enterprise clinical data warehouse, for calendar year 2010 on approximately 23,000 patients (Pfaff et al., under review in *JAMIA*).

Together, CAMP FHIR and FHIR PIT are being used to create integrated feature tables as part of Green Team's [Integrated Clinical and Environmental Exposures Service](https://github.com/ResearchSoftwareInstitute/data-translator/tree/master/src/pages/apps/icees).

**Generalizability**
We believe that the use of CAMP FHIR to harmonize clinical data will save institutional resources over the alternative of standing up new CDMs to support multi-institutional collaborations. Moreover, using FHIR as a CDM could support rarer data sharing opportunities, such as collaborations between academic medical centers and community hospitals, thus democratizing participation and access. Moreover, we anticipate adoption and use of CAMP FHIR to stimulate the vision of the Translator program, foster clinical and translational research at UNC and elsewhere, and promote the broader vision of NCATS, particularly with respect to the CTSAs.


**GitHub Repo**

CAMP FHIR is freely accessible. A [CAMP FHIR GitHub repository](https://github.com/NCTraCSIDSci/camp-fhir) provide access to PCORnet mappings as “starter scripts” to acclimate new users to the tool. In order to use CAMP FHIR, users run these scripts (or their own versions) to create views within their source database that conform to our CAMP FHIR standard, populate a code mapping table for any value sets, and point CAMP FHIR at the database.
