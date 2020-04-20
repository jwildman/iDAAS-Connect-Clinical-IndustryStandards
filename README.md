# Background
For decades across the various markets within healthcare (clinical, financial, pharmacy and life sciences) integration has been a challenge for many differnt reasons. Within Red Hat there is a specific industry team dedicated to ensuring Red Hat's technologies meet the industry needs and ensuring its customers have meaningful platforms that demonstrate these capabilities. The Red Hat healthcare team, has had a specific interest in enabling and empowering healthcare organizations to transform their integration efforts while also introducing and infusing Red Hat's open organization, open source mindset and community based culture as well. As the Red Hat healthcare team started this journey they also wanted to ensure they could help showcase integration as an innovation enabler and helping simplify IT.

As discussed in the introduction integration has been a challenge for decades in each market within healthcare. Within healthcare the challenges have been driven by many different factors, here are just a few common ones: industry standards (HL7) that aren't constrained enough, Clincal software vendor market constraints, COTS integration vendor lock-in, and government mandates that they cannot directly support without third party vendor engagement.

As the Red Hat healthcare team thought about potential ways to help the clinical integration space, they came up 
some differentiators for whatever gets built:

* Extenibility
* Reduce Proprietary Knowledge
* Open Source Enablement
* Modern Application Development/Delivery Capabilities
* Reduce Propritary Skillset(s)
* Deliver Consistentcy
* Polyglot Language Support

Here's how the differentiators are being addressed:

* Extensibility: The fovus has been on building an extensible platform. The platform is just a series of components that can be connected, extended or new components developed as developers and business teams work together. 
* Reduce Proprietray Knoweldge: We have removed COTS or black box box software and gone with a very open approach. Spring Boot, Postgres/mariaDB/SQL Server, Red Hat Fuse, Red Hat Process Automation Manager (Business Rules, Workflow and Complex Event Processing), Red Hat A-MQ (soon we are also puttting in AMQ-Streams).
* Open Source Enablement: Provide the source code of the components to extend as needed. Currently, the code is in Git Hub private repos currently as we work through some processes.
* Modern Application Development/Delivery Capabilities: Where applicable everything is cloud native/container focused. Several of the platform components are based on SpringBoot for easy of deployment and running.
* Reduce Preprietary Skillsets: Removing COTS centric skillsets.
* Deliver Consistency: Focus around industry standard design and integration patterns.
We don't require deep knowledge of the industry standards to get started, just common developer skillsets. 
* Polyglot Language Support: Enabling the use of many different programming languages. The focus here is to ensure by major capability area a programming language is supported.

# Platform: Connected Health / iDAAS 
As part of the general vision for healthcare, the Red Hat healthcare team established a extensible platform, Connected Health/iDAAS (Intelligent Data As A Service). Connected Health/iDAAS overall objective is to simplify data integration and interoperability needs. By establishing a platform initally this enabled the team to focus on the overall industry needs and work through them and establish capabilities for each. As the capabilities were worked through components have been developed to address these needs. 

Here is a general visual of how iDAAS fits in and can enable innovation and solving the problem of integration innovation in the clinical space:
<p align="center" >
<img src="https://github.com/balanscott/iDAAS-Connect-Clinical/blob/development/content/images/iDAAS%20-%20High%20Level%20Solution%20Overview.png/" alt="Healthcare Integration" width="500" height="350" />
</p>

# Data Enablement: iDAAS Connect Clinical 
The problem of healthcare connectivity and data enablement has been around for decades. Vendors have had long standing practices of limiting paying customers to the data within the systems they operate and manage. As healthcare organizations prepare for their digital experiences this is no longer a practice that can be tolerated or endured. The solution for data enablement is iDAAS Connect Clinical.

As you look at this repository please keep in mind it is the code that powers the clinically connectivity component of the iDAAS Platform, iDAAS Connect Clinical. It has been designed and developed to support Clinical Integration standards based data exchanges and perform an enterprise clinical integration pattern for routing of data. From an integration connectivity and standards perspective it can demonstrates the processesing HL7v2 messages of the following types from any vendor and any specifc message version from 2.1 to 2.8: ADT (Admissions), ORM (Orders), ORU (Results), SCH (Schedules), PHA (Pharmacy), MFN (Master File Notifications), MDM (Medical Document Management) and VXU (Vaccinations). We are actively working on adding in FHIR R4 support. 

# Industry Standard Support
As mentioned above we discussed the industry Standard support. This section covers the clinical integration standards and detailed links that are support by the implementation of the platform:

* [HL7 v2 Message Receivers](https://www.hl7.org/implement/standards/product_brief.cfm?product_id=185 "HL7 v2 Message Receivers") - Support for ADT, ORM, ORU, RDE, SCH, MFN, MDM and VXU message types. Connected Clinical does not care about specific HL7 version, its has been tested from version 2.1 through 2.8.
* [FHIR Clinical Receivers](https://www.hl7.org/fhir/ "HL7 FHIR") - Support for FHIR Clinical is currently being implemented. The platform will focus on delivery R4 (4.01) support to align with the CMS guidance on Interoperability and Patient Access. 

# General Capabilities
General Capabilities that are implemented in the platform:

* [Healthcare Streaming Event Support](https://www.redhat.com/en/technologies/jboss-middleware/amq "Streaming Technologies") - Support decoupled and/or streaming architecture.
* Healthcare Event Support - Support for building, extending and enabling healthcare event processing.
* Architecture designed for extensibility, enhancement and massive scale.

# Development IDE
The iDAAS (Intelligent Data as a Service) Clinical platform was initially developed using Eclipse. While this can still be used to update code, the team wanted to share its has transitioned to the following Development IDE and plugins: 

* IntelliJ Community IDE
* Apache Camel Plugin
* Big Data Tools Plugin
* Kubernetes Plugin

# iDAAS Technologies
The iDAAS (Intelligent Data as a Service) Clinical platform is intended for usage for the healthcare market. It contains the following Red Hat technologies, (this platform will also will work with their upstream equivalents):

* Red Hat Fuse
* Red Hat Process Automation Manager
* Red Hat A-MQ
* Red Hat OpenShift

It contains the following non Red Hat technologies:

* Java
* Spring Boot
* Maven 


# Practical Implementation: Partnering Organization
To support ANY developed artifcats the Red Hat Healthcare team has created a fictious company named Care Delivery Corporation US (CADuCeUS). Care Delivery Corp. US is intended to be a multi-faceted healthcare organization with businesses and needs across all healthcare markets. 

Healthcare Facilities:  MCTN   
Sending Application:    MMS (Main Medical Software)
Custom Application:     myEHR

# Other Contributions within Source

While this repository has all the source code needed to run the solution, it also has several additional artifacts within specific  directories that are needed to run the code:

* amq: This directory is for the amq based implementation of iDAAS, iDAAS currently is implemented with Kafka. The amq directory contains the broker script that can be implemented within the A-MQ area created when you did ./artemis create <amqArea> and you just need to place the broker.xml file from this directory in its <path to A-MQ>/<amqArea>/bin
* content-published: This directory is intended to maintain any content published about the platform.

# Building

This code can be built with the following command:

mvn clean install

# Running


# Containers Based - Openshift (where possible) 
It is assumed that:

OpenShift platform is already running, if not you can find details how to Install OpenShift at your site.
Your system is configured for Fabric8 Maven Workflow, if not you can find a Get Started Guide
The example can be built and run on OpenShift using a single goal:

mvn fabric8:deploy
When the example runs in OpenShift, you can use the OpenShift client tool to inspect the status

To list all the running pods:

oc get pods
Then find the name of the pod that runs this quickstart, and output the logs from the running pods with:

oc logs <name of pod>
You can also use the OpenShift web console to manage the running pods, and view logs and much more.

Running via an S2I Application Template

Application templates allow you deploy applications to OpenShift by filling out a form in the OpenShift console that allows you to adjust deployment parameters. This template uses an S2I source build so that it handle building and deploying the application for you.

First, import the Fuse image streams:

oc create -f https://raw.githubusercontent.com/jboss-fuse/application-templates/GA/fis-image-streams.json
Then create the quickstart template:

oc create -f https://raw.githubusercontent.com/jboss-fuse/application-templates/GA/quickstarts/spring-boot-camel-template.json
Now when you use "Add to Project" button in the OpenShift console, you should see a template for this quickstart.

# Other Related GitHub Repositories for Connected Health / iDAAS Platform Components
As mentioned above iDAAS is a platform and is built in a very modular manner. Below is a detailed set of links to all the other iDAAS GitHub repositories and their purpose. 

| iDAAS Platform Component | iDAAS Repository Link | Description |
| ------------------------ | --------------------- | ----------- |
| iDAAS Event Builder      | https://github.com/balanscott/iDAAS-EventBuilder  | All the Parsers and Pojos used by the iDAAS platform, it can be referenced in any other iDAAS Platform component |
| iDAAS Data Integration Event Builder  | https://github.com/balanscott/iDAAS-DataIntgrtn-EventBuilder | Data Integration framework to handle various forms of streaming data and invoke iDAAS Event Builder to output healthcare events |
| iDAAS Data DataHub | https://github.com/balanscott/iDAAS-Data-DataHub | Specific tier for ensuring end users can see transactions the platform has processed and reports. This is comprised on a scalable integration project and also includes the DDL for Postgres and SQL Server |
| iDAAS Visual UI | https://github.com/balanscott/iDAAS-Visual-UI | Visual Tier for representing the platforms data and providing insight and related capabilities |
| iDAAS Message Simulator | https://github.com/balanscott/MessageSimulator | This is currently a very small .Net Core console application. The intent is to grown and extend it to a feature rich component set for all iDAAS message testing needs |
