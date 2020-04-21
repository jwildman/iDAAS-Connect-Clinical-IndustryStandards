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
* Innovative Disruption
* Deliver Consistentcy
* Polyglot Language Support

Here's how the differentiators are being addressed:

* Extensibility: The focus has been on building an extensible platform based on need and usage. The platform is just a series of components that can be connected, extended or new components developed as developers and business teams work together. Within the platform it is developed to enable small to large and complex healthcare organizations to leverage this platform. The platform looks at ANY data as by the application, components, facilities, and overall organization associated with EVERY transaction. 
* Reduce Proprietray Knoweldge: We have removed COTS or black box box software and gone with a very open approach. Our approach leverages the numerous Open Source and upstream Open Source products Red Hat is engaged in. Here are several of the technologies this platform leverages: Spring Boot, Red Hat Fuse, Red Hat Process Automation Manager (Business Rules, Workflow and Complex Event Processing), Red Hat A-MQ Streams (Kafka)  - (we also into an A-MQ release as well).
* Open Source Enablement: Provide the source code of the components to extend as needed.
* Modern Application Development/Delivery Capabilities: Where applicable everything is cloud native/container focused. Several of the platform components are based on SpringBoot for easy of deployment and running.
* Reduce Preprietary Skillsets: Removing COTS centric skillsets. This platform is about enabling industry best technologies to enable healthcare to build capabilities rapidly. 
* Disruption: This platform is absolutely designed to enable disruption and enable innovation at the speed of business and technologists.
* Deliver Consistency: Focus around industry standard design and integration patterns.
We don't require deep knowledge of the industry standards to get started, just common developer skillsets. 
* Polyglot Language Support: Enabling the use of many different programming languages. The focus here is to ensure by major capability area a programming language is supported.

# Platform: Connected Health / iDAAS 
As part of the general vision for healthcare, the Red Hat healthcare team established a extensible platform, Connected Health/iDAAS (Intelligent Data As A Service). Connected Health/iDAAS overall objective is to simplify data integration and interoperability needs. By establishing a platform initally this enabled the team to focus on the overall industry needs and work through them and establish capabilities for each. As the capabilities were worked through components have been developed to address these needs. 

Here is a general visual of how iDAAS fits in and can enable innovation and solving the problem of integration innovation in the clinical space:
<p align="center" >
<img src="https://github.com/balanscott/iDAAS-Connect-Clinical/blob/development/content/images/iDAAS%20-%20High%20Level%20Solution%20Overview.png/" alt="Healthcare Integration" width="500" height="350" />
</p>

Here is a specific visual on the iDAAS Platform and all its specific components:
<img src="https://github.com/redhat-healthcare-chiefarchitect/iDAAS-Connect-Clinical-IndustryStds/blob/development/content/images/iDAASPlatform-Tier_High%20Level.png/" alt="iDAAS Component Design" 
width="500" height="350" />

# Data Enablement: iDAAS Connect Clinical Industry Standards
The problem of healthcare connectivity and data enablement has been around for decades. Vendors have had long standing practices of limiting paying customers to the data within the systems they operate and manage. As healthcare organizations prepare for their digital experiences, or look to re-evaluate their current digital experience capabilities, this is no longer a practice that can be tolerated or endured. Within iDAAS, this is the component responsible for providing connectivity to the clinical based industry standards of HL7 v2 messages and FHIR. From an integration connectivity and standards perspective it can demonstrates the processesing HL7v2 messages of the following types from any vendor and any specifc message version from 2.1 to 2.8: ADT (Admissions), ORM (Orders), ORU (Results), SCH (Schedules), PHA (Pharmacy), MFN (Master File Notifications), MDM (Medical Document Management) and VXU (Vaccinations). With the final CMS rule around Interoperability we have also added FHIR R4 Support. 

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
* Red Hat A-MQ Streams
* Red Hat OpenShift

It contains the following non Red Hat technologies:

* Java
* Spring Boot
* Maven 

# Practical Implementation: Partnering Organization
To support ANY developed artifcats the Red Hat Healthcare team has created a fictious company named Care Delivery Corporation US (CADuCeUS). Care Delivery Corp. US is intended to be a multi-faceted healthcare organization with businesses and needs across all healthcare markets. This way, ALL the source code/demonstrations and documentation focus on specific healthcare market needs.

Healthcare Facilities:  MCTN   
Sending Application:    MMS (Main Medical Software)
Custom Application:     myEHR

# Other Contributions within Source

While this repository has all the source code needed to run the solution, it also has several additional artifacts within specific  directories that are needed to run the code:

* amq: This directory is for the amq based implementation of iDAAS, iDAAS currently is implemented with Kafka. The amq directory contains the broker script that can be implemented within the A-MQ area created when you did ./artemis create <amqArea> and you just need to place the broker.xml file from this directory in its <path to A-MQ>/<amqArea>/bin
* content-published: This directory is intended to maintain any content published about the platform.

# Building and Running

This code can be built with the following command:

mvn clean install


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
As mentioned above iDAAS is a platform and is built in a very modular manner. We will be releasing other public Git Hub repositories that will enable additional extensibility.
