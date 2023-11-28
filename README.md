# EVOLVED-5G overview
The EVOLVED-5G architecture is built around four major environments: Workspace, Validation, Certification and Marketplace.

![EVOLVED-5G Architecture](./images/architecture.png)

Following the numbers from the image, four environments are described starting from the Workspace.
### Workspace Environment

The workspace is one of the core architectural environments of the NetApsds ecosystem. The main objective of the Workspace environment is to provide developers with the necessary software tools and instructions for Network Applications development while making this process easy, quick and convenient. To do so, it goes through two phases; namely, the Network Applications development and verification phases. 

The Development phase is one of the Workspace main functional blocks. The objective of the Development phase is to help developers to develop the Network Applications by providing the necessary means, e.g., within the scope of the SDK tools, the developers will be provided with some libraries to enhance the Network Applications with the 5G capabilities which in following phases will be tested. 

The purpose of the Development phase is to provide a fully Network Applications with a readiness level to besent to the next phase which will be verification.

The Verification phase is formed by the CI/CD Services and the Emulation Environment
functional blocks. The CI/CD services is in charge to run the pipeline; the Emulation Environment is responsible of performing the defined tests for verification.

The objective of the Verification phase is to guarantee that the Network Applications is able to operate correctly in a synthetic environment before releasing it to the Validation environment where functional and non-functional tests are provided. During the verification phase only the Network Applications itself is considered and not any potential vApp that could be associated to it.

The Workspace environment also provides developers with the appropriate code storage repository
(GitHub) where tools and instructions are stored as well as the code of the Network Applications generated during the development phase, and an artifact repository (Open Repository) and a Docker Registry where the binaries coming from the verification phase will be stored.

### Validation Environment

The Validation environment is the functional block that is in charge of the validation of the Network Applications. The goal of the Validation environment is to provide the tools and methodology required for the execution of the validation process. The validation process includes the evaluation of the functionality of the Network Applications when they are used along with the vertical App (vApp) on the platform (Athens or Malaga )as well as performance tests.

Within the lifecycle of a Network Applications, the Validation environment is used after a successful
completion of the verification process, i.e., only after a prove that the Network Applications is functional and compatible with the 5G APIs. Similarly, the successful completion of the validation process is a pre-condition for a Network Applications to enter the certification process.

### Certification Environment

 This certification environment enables the construction of the certification process. This environment is composed of a set of tools that allow the creation of an Evolved-5G area where all the tools to build the certification process and execute Network Applications certifications are integrated. The tools are as follows: 

 * Continuois Integration / Continuous Delivery (CI/CD) process for delivering applications frequently.
 * The Open Repository to store artifacts.
 * Jenkins for Pipelines Automation.
 * Terraform to manage the Infrastructure as Code.
 * Robot FramekworkFramework to build automated test .

 The Certification process is responsible for certifying that Network Applications meet the Eveolved5G criteria defined to consider a Network Applications as Evolved5G. This criterion is based on the following principles: 

 * Network Applications is secure.
 * Network Applications can be deployed in a cloud infrastructure. 
 * The Network Applications is cloud-native.  
 * Network Applications uses CAPIF APIs to discover and consume APIs. 
 * Network Applications uses NEF APIs to interact with the 5G infrastructure. 


### Marketplace Environment

Evolved-5G Marketplace is an online, cross-industry API Marketplace that enables developers, entrepreneurs and businesses to come together to create, discover and integrate services by consuming the Network Applications that have been created in the Evolved-5G ecosystem. 

## Main features

The EVOLVED-5G facility provides different tools/software to allow the lifecycle of a Network Applications. Such software are list as follows:

### SDK

The Software Development Kit (SDK) is one of the functional blocks of the Workspace, which provides a set of tools to facilitate the development of Network Applications for developers. The tools integrated in the SDK are the following: 

* A SDK CLI tool, which allows the developer to create the repository for each Network Applications from an automated Network Applications template. Provide 5G Core libraries and launch pipelines for verification purposes.
* SDK Libraries, that facilitate the interaction of Network Applications developers with either our NEF emulator or a real Core 5G, by providing an abstraction towards the use of APIs.
* Network Applications Template, where the developer can find the structure of folders and files that compose the Network Applications. This template is mainly made up of another tool called Cookiecutter.


###  Network App Template

Network App template is a Github repository, from which you can create a new repository with a folder and file structure. In the Network Applications template you can find the structure of a Network Applications as well as the files of the Cookiecutter tool.

Cookiecutter is a Python-based command line tool to create projects from a template. Cookiecutter files are in the Network Applications template to run in the SDK to generate the Network Applications structure by populating it with the entries requested by Cookiecutter when it runs.  Also, a python script allows to upload the new repository to GitHub.

### Common API Framework (CAPIF) tool

The main purpose of CAPIF is to have a unified north bound API framework across several 3GPP functions. There is a single and harmonized approach for API development, with a number of 3GPP specifications on the work – to specify a framework to host APIs of PLMN and also to allow for third parties to leverage the CAPIF framework to host their APIs [Common API Framework](https://www.3gpp.org/common-api-framework-capif).

The CAPIF tool has been developed in the context of EVOLVED-5G for the Verification, Validation and Certification process.
and certification process. The CAPIF tool is an implementation of the CAPIF APIs for the CAPIF Core entity. This tool implements a REST API server that
accepts API requests from the CAPIF entities defined as API Invokers, API Exposing Function, API Publishing Function and API Management function.
Publishing Function and API Management function


### Network Function Exposure (NEF) emulator  

The Network Function Exposure (NEF) is the Northbound interface between the NEF and the Application Function (AF). It specifies RESTful APIs that allow the AF to access the services and capabilities provided by 3GPP network entities and securely exposed by NEF [Network Exposure Function](https://www.etsi.org/deliver/etsi_ts/129500_129599/129522/16.04.00_60/ts_129522v160400p.pdf).In EVOLVED-5G we have developed and implement a NEF emulator software to emulate the Northbound APIs of 3GPP’s.

It mainly follows the RESTful paradigm and provides Network Applications with some of the internal services and capabilities that the 5G System (5GS) offers. NEF emulator provides tools for simulating events (e.g., mobility aware event where UEs are moving in predefined paths).

### Time Sensitive Networking (TSN) FrontEnd
Exposes an API to request network configurations related to TSN and deterministic communication. There is a set of pre-defined configurations which can then be customized by developers.

### Dummy Network App

Dummy Network App is an example of a Network App within the EVOLVED-5G framework. It has been implemented to help developers. It implements all the functionalities developed in EVOLVED-5G, i.e., making use of the SDK libraries and following the structure files provided by the Network Applications template. The repository can be found here:[Dummy Network Applications](https://github.com/EVOLVED-5G/dummy-network-application)

### CI/CD  and Jenkins Pipelines
Continuous Integration / Continuous Delivery (CI/CD) is a method for delivering applications frequently. For this, automation is applied in the stages of application development. The key concepts attributed to this method are continuous integration, delivery and deployment.

The Network Applications lifecycle in EVOLVED-5G has three phases: Verification, Validation and Certification. Each of these phases will have a separate process supported by CICD tools. 

Evolved5G uses Jenkins as its pipeline automation tool. Jenkins is a free and eopen-source automation server, which helps to automate continuous integration and facilitating continuous delivery. It supports version control tools, including Git. Builds can be triggered by various means, for example by commit in a version control system, by scheduling via a cron-like mechanism and by requesting a specific build URL. It can also be triggered after the other builds in the queue have completed. Jenkins functionality can be extended with plugins.

Pipeline configuration in Jenkins enables to define the whole Network Applications lifecycle defined in Evolved5G. The pipeline plugin was built with requirements for a flexible, extensible, and script-based Continous Deployment workflow capability in mind. 

## EVOLVED-5G Service Package
The EVOLVED-5G Service Package is a software bundle to facilitate developers for the creation, verification[^1], validation[^1] and certification[^1] of Network Applications. It is Virtual Machine (VM) as a downloadable package to be installed for local use. The EVOLVED-5G Service Package ease and allows developers to initiate in the development of Network Applications. 
The EVOLVED-5G Service Package includes the SDK, the Network App template, CAPIF, NEF, TSN and the Dummy Network App. Therefore, the developer can interact with the Dummy Network App to understand how a Network App communicates with NEF and TSN through CAPIF.
Developers can download the VM from the following <a href="http://aias.iit.demokritos.gr/~koumaras/evolved-5g/">link</a> and import it to their preferred hypervisor.

[^1]: This Service Package also includes processes for Network App verification, validation and certification. Please, have in mind that once the project has finished is mostly probable that some of such features are not available anymore. Please send an email to approval@evolved-5g.eu to know the status of such features.
