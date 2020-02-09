# WebLogic Docker Deployment Demo

This demo illustrates how to deploy applications to WebLogic Docker image

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

- Prepare a script called 'run.sh' with the following content:

```
docker container run -d -p 7001:7001 -p 9001:9002 -it --name weblogic -v <local_dir_container_domain.properties>:/u01/oracle/properties -e DOMAIN_NAME=<domain_name> store/oracle/weblogic:12.2.1.4-dev-200117
```

Replace the environment specific variables in <> above accordingly to match your local environment and desired new domain name.

- Run the above script to start WebLogic container
- Note that default admin console port at 7001 is disabled by default, and you need to access WebLogic console via https://<host_name>:9001/console instead. Login to the admin console with the above ID/password
- Also note that for simplicity, this demo only guides you create a WebLogic domain with admin server only and deploy applications on Admin Server. For production, you should be creating a cluster and deploy applications ONLY to managed servers instead of Admin Server. More details are available in the Getting Started section of WebLogic Docker image from DockerHub

3. Deploy Applications

- You can now deploy any application you want to the container from WebLogic console

4. [Optional] Should you want to create a new image based on the updated container (with apps deployed), you can refer to guide in https://github.com/yyeung13/oke_ocir_demo/blob/master/customise_tomcat.MD Step 2 for details
