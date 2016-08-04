# SAP Inside Track Registration app backend

This repository contains the backend for the SITreg app. It is developed on SAP HANA native using XSODATA. For more details check out the information in the [Wiki](https://github.com/sapmentors/SITreg/wiki). You can find the frontend projects here:

* [SITregParticipant](https://github.com/sapmentors/SITregParticipant)
* [SITregOrganizer](https://github.com/sapmentors/SITregOrganizer)

## Setup Guide

### Backend

You must have developer authorization in your HANA System. To try this project just spin up your own HANA Multitennant Database Container (MDC) on the [HANA Cloud Platform Trial (HCP)](https://hcp.sap.com/). Open the SAP HANA Web-based Development Workbench and create the package:

    com/sap/sapmentors/sitreg

After you've created the package right click on the **sitreg** package and choose **Syncronize with GitHub**. Provide your GitHub credentials to allow the HANA system to read your GitHub repositories. As you can't specify a GitHub repository URL you have to fork the project so you have it in your repository list. Then coose the cloned repository and GitHub branch **master**. Click **Fetch** to retreive the content. After that step you have to activate the artifacts. Try a right click **activate all**.

To test the different services with the correct authorizations setup the users: 

* PARTICIPANT 
* ORGANIZER
* COORGANIZER
* SITREGADMIN
 
Assign the roles:

* com.sap.sapmentors.sitreg.roles::participant (to PARTICIPANT)
* com.sap.sapmentors.sitreg.roles::organizer (to ORGANIZER and COORGANIZER)
* com.sap.sapmentors.sitreg.roles::admin (to SITREGADMIN)

to be able to test the different services also according the correct implementation of the authorizations.

### Frontend

To be able to test the two frontend apps with the backend you have to create a destination in the **SAP HANA Cloud Platform Cockpit**. If you adjust the following and save it in a file called **HANAMDC** you can use the **Import Destination** function. After that you only have to maintain the password for your user.

```
Type=HTTP
Authentication=BasicAuthentication
Name=HANAMDC
WebIDEEnabled=true
URL=https\://<your-hana-mdc-host>.hanatrial.ondemand.com
ProxyType=Internet
User=<your-user>
WebIDESystem=HANAMDC
```

If you want to use the HANA MDC XSODATA Service in a HCP HTML5 app with App2AppSSO then follow the great Blog by Martin Raepple: [Principal Propagation between HTML5- or Java-based applications and SAP HANA XS on SAP HANA Cloud Platform](http://scn.sap.com/community/developer-center/cloud-platform/blog/2016/03/21/principal-propagation-between-html5-and-sap-hana-xs-on-sap-hana-cloud-platform). After you've did the setup you can adjust your destination and set

```
Authentication=AppToAppSSO
```
