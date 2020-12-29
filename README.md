# Introduction
This is for Jboss/wildfly Interview questions and demo


# 问题
## What is the directory structure in JBoss?
- modules
- bundles
- domain
- standalone
- appclient
- bin
- docs
- welcome-content

## Which component is responsible for handling clustering?
JBoss clustering is on top of JGroups toolkit which helps to create, delete, membership detection, notification, etc. in the cluster.
## What’s the default port to access Administration Console in JBoss 7?
9990 is the default port. If it’s installed on server1 then you need to access like:

    http://server1:9990/admin-console
## What must be done to access Admin Console?
The user must be created under “ManagementRealm” to have console operational. To create the user, you can go to bin folder and execute add-user.sh/bat script.
## How to find account and password for console?
Passwords by default are stored in

    $WILDFLY_HOME/standalone/configuration/mgmt-users.properties
but passwords are hashed. Best thing you can do is to remove the user you want and then re-add it via add-user.sh/.bat script you can find in bin folder.

account: admin

password: admin
## How to start JBoss in standalone mode?
Go to the bin folder where JBoss is installed and start with the following command.
   
   ./standalone.sh
   
   standalone.bat
## How to increase Java Heap Memory in JBoss 7?
   Heap Memory can be increased in a respective conf file. To increase memory for standalone;
   
   Go to the bin folder
   Edit the standalone.conf file and look for “JAVA_OPTS=” argument line
   The default configuration will have a minimum of 64 MB and a maximum of 512 MB. You can increase to the desired value.
   Xms – specify the minimum heap size 
   Xmx – specify the maximum heap size

## What is the difference between standalone and domain mode?
Standalone mode is single JVM process where every JBoss server has its configuration. If you just need one JVM or development environment, then standalone would be perfect.

Domain mode may have multiple servers where all configuration is managed centralized and often used in production environment.

## Can you create a cluster in standalone mode?
   Yes, clustering is possible in standalone mode. However, an application must be deployed on each server/JVM in standalone mode.
## What are the file types you can deploy in JBoss?
You can deploy almost any kind of Java/J2EE application, and it supports the following file format.

    WAR – Web application archive
    SAR – Service archive
    JAR – Java Archive
    EAR – Enterprise application archive

## How can you deploy an application?
   There are three possible ways to deploy an application in JBoss application server.
   
   Admin Console – you can deploy the necessary application files through the administration console.
   Auto-deploy – leverage file system deployment scanner to auto-deploy files from the deployments folder.
   Automation – use automation tool/ant/scripting to deploy an application.
   
## What marker file type is required to instruct JBoss to deploy?
.dodeploy file suffix is needed for JBoss to deploy or redeploy an application.

Ex:

    myfirstapplication.war.dodeploy

## What are the important types available for marker file deployment?
   .dodeploy – instruct to deploy
   .deployed – indicate the file is deployed
   .pending – deployment is still pending
   .undeployed – confirmation that application is undeployed
   .failed – deployment is failed for some reason
   .skipdeploy – instruct JBoss to ignore the files for auto-deployment

## What does mgmt-user.properties contain?
   All admin console users and passwords (encrypted) are stored in mgmt.-user.properties file.