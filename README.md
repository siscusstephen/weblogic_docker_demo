# WebLogic Docker Deployment Demo

This demo illustrates how to deploy applications to WebLogic Docker image and push the completed image to OCIR

## Pre-Requisite

You need to have DockerHub account and have Docker installed in the environment you are running on before proceeding with the demo steps below. In case you need help with Docker installation on Oracle Enterprise Linux, please refer to https://blogs.oracle.com/blogbypuneeth/a-simple-guide-to-docker-installation-on-oracle-linux-75

## Demo Details

1. Pull WebLogic Docker Image from DockerHub

- Login to http://hub.docker.com
- Search for 'weblogic' from search bar on top of the screen and click on official WebLogic image from Oracle
- Click button 'Proceed to checkout' from right hand side, fill in contact information, agrees on T&Cs and click 'Get Content'
- Take note of the docker pull command on the right hand side, e.g., 'docker pull store/oracle/weblogic:12.2.1.4-dev-200117'
- Run the docker pull command to pull WebLogic Docker Image.
- Confirm the image is downloaded by running 'docker images' and verify weblogic image can be found.

2. Start WebLogic Server container from WebLogic image

- Create a local folder to store configuration and scripts for starting WebLogic container, e.g., $HOME/weblogic
- Create a file called domain.properties within the folder with the following content:
```
username=weblogic
password=welcome1
```
  User name above is 'weblogic' and password is set to 'welcome1', you can choose your own password accordingly.


3. Deploy Applications


