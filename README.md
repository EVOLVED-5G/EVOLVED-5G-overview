# EVOLVED-5G overview
The EVOLVED-5G architecture is built around four major environments: Workspace, Validation, Certification and Marketplace.

![EVOLVED-5G Architecture](./images/architecture.png)

Following the numbers from the image, four environments are described starting from the Workspace.
### Workspace Environment

The workspace is one of the core architectural environments of the NetApsds ecosystem. The main objective of the Workspace environment is to provide developers with the necessary software tools and instructions for NetApp development while making this process easy, quick and convenient. To do so, it goes through two phases; namely, the NetApp development and verification phases. 

The Development phase is one of the Workspace main functional blocks. The objective of the Development phase is to help developers to develop the NetApp by providing the necessary means, e.g., within the scope of the SDK tools, the developers will be provided with some libraries to enhance the NetApp with the 5G capabilities which in following phases will be tested. 

The purpose of the Development phase is to provide a fully NetApp with a readiness level to besent to the next phase which will be verification.

The Verification phase is formed by the CI/CD Services and the Emulation Environment
functional blocks. The CI/CD services is in charge to run the pipeline; the Emulation Environment is responsible of performing the defined tests for verification.

The objective of the Verification phase is to guarantee that the NetApp is able to operate correctly in a synthetic environment before releasing it to the Validation environment where functional and non-functional tests are provided. During the verification phase only the NetApp itself is considered and not any potential vApp that could be associated to it.

The Workspace environment also provides developers with the appropriate code storage repository
(GitHub) where tools and instructions are stored as well as the code of the NetApps generated during the development phase, and an artifact repository (Open Repository) and a Docker Registry where the binaries coming from the verification phase will be stored.

### Validation Environment

The Validation environment is the functional block that is in charge of the validation of the NetApp. The goal of the Validation environment is to provide the tools and methodology required for the execution of the validation process. The validation process includes the evaluation of the functionality of the NetApps when they are used along with the vertical App (vApp) on the platform (Athens or Malaga )as well as performance tests.

Within the lifecycle of a NetApp, the Validation environment is used after a successful
completion of the verification process, i.e., only after a prove that the NetApp is functional and compatible with the 5G APIs. Similarly, the successful completion of the validation process is a pre-condition for a NetApp to enter the certification process.

### Certification Environment

 This certification environment enables the construction of the certification process. This environment is composed of a set of tools that allow the creation of an Evolved-5G area where all the tools to build the certification process and execute NetApp certifications are integrated. The tools are as follows: 

 * Continuois Integration / Continuous Delivery (CI/CD) process for delivering applications frequently.
 * The Open Repository to store artifacts.
 * Jenkins for Pipelines Automation.
 * Terraform to manage the Infrastructure as Code.
 * Robot FramekworkFramework to build automated test .

 The Certification process is responsible for certifying that NetApps meet the Eveolved5G criteria defined to consider a NetApp as Evolved5G. This criterion is based on the following principles: 

 * NetApp is secure.
 * NetApp can be deployed in a cloud infrastructure. 
 * The NetApp is cloud-native.  
 * NetApp uses CAPIF APIs to discover and consume APIs. 
 * NetApp uses NEF APIs to interact with the 5G infrastructure. 


### Marketplace Environment

Evolved-5G Marketplace is an online, cross-industry API Marketplace that enables developers, entrepreneurs and businesses to come together to create, discover and integrate services by consuming the NetApps that have been created in the Evolved-5G ecosystem. 

## Main features

The EVOLVED-5G facility provides different tools/software to allow the lifecycle of a NetApp. Such software are list as follows:

### SDK

The Software Development Kit (SDK) is one of the functional blocks of the Workspace, which provides a set of tools to facilitate the development of NetApps for developers. The tools integrated in the SDK are the following: 

* A SDK CLI tool, which allows the developer to create the repository for each NetApp from an automated NetApp template. Provide 5G Core libraries and launch pipelines for verification purposes.
* SDK Libraries, that facilitate the interaction of NetApps developers with either our NEF emulator or a real Core 5G, by providing an abstraction towards the use of APIs.
* NetApp Template, where the developer can find the structure of folders and files that compose the NetApp. This template is mainly made up of another tool called Cookiecutter.


###  NetApp Template

NetApp template is a Github repository, from which you can create a new repository with a folder and file structure. In the NetApp template you can find the structure of a NetApp as well as the files of the Cookiecutter tool.

Cookiecutter is a Python-based command line tool to create projects from a template. Cookiecutter files are in the NetApp template to run in the SDK to generate the NetApp structure by populating it with the entries requested by Cookiecutter when it runs.  Also, a python script allows to upload the new repository to GitHub.

### CAPIF tool

The main purpose of CAPIF is to have a unified north bound API framework across several 3GPP functions. There is a single and harmonized approach for API development, with a number of 3GPP specifications on the work ??? to specify a framework to host APIs of PLMN and also to allow for third parties to leverage the CAPIF framework to host their APIs [Common API Framework](https://www.3gpp.org/common-api-framework-capif).

The CAPIF tool has been developed in the context of EVOLVED-5G for the Verification, Validation and Certification process.
and certification process. The CAPIF tool is an implementation of the CAPIF APIs for the CAPIF Core entity. This tool implements a REST API server that
accepts API requests from the CAPIF entities defined as API Invokers, API Exposing Function, API Publishing Function and API Management function.
Publishing Function and API Management function


### NEF emulator  

The Network Function Exposure (NEF) is the Northbound interface between the NEF and the Application Function (AF). It specifies RESTful APIs that allow the AF to access the services and capabilities provided by 3GPP network entities and securely exposed by NEF [Network Exposure Function](https://www.etsi.org/deliver/etsi_ts/129500_129599/129522/16.04.00_60/ts_129522v160400p.pdf).In EVOLVED-5G we have developed and implement a NEF emulator software to emulate the Northbound APIs of 3GPP???s.

It mainly follows the RESTful paradigm and provides NetApps with some of the internal services and capabilities that the 5G System (5GS) offers. NEF emulator provides tools for simulating events (e.g., mobility aware event where UEs are moving in predefined paths).

### Dummy NetApp

Dummy NetApp is an example of a NetApp within the EVOLVED-5G framework. It has been implemented to help developers. It implements all the functionalities developed in EVOLVED-5G, i.e., making use of the SDK libraries and following the structure files provided by the NetApp template. The repository can be found here:[Dummy NetApp](https://github.com/EVOLVED-5G/dummy-netapp)

### CI/CD  and Jenkins Pipelines
Continuous Integration / Continuous Delivery (CI/CD) is a method for delivering applications frequently. For this, automation is applied in the stages of application development. The key concepts attributed to this method are continuous integration, delivery and deployment.

The NetApp lifecycle in EVOLVED-5G has three phases: Verification, Validation and Certification. Each of these phases will have a separate process supported by CICD tools. 

Evolved5G uses Jenkins as its pipeline automation tool. Jenkins is a free and eopen-source automation server, which helps to automate continuous integration and facilitating continuous delivery. It supports version control tools, including Git. Builds can be triggered by various means, for example by commit in a version control system, by scheduling via a cron-like mechanism and by requesting a specific build URL. It can also be triggered after the other builds in the queue have completed. Jenkins functionality can be extended with plugins.

Pipeline configuration in Jenkins enables to define the whole NetApp lifecycle defined in Evolved5G. The pipeline plugin was built with requirements for a flexible, extensible, and script-based Continous Deployment workflow capability in mind. 