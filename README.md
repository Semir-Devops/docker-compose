# docker-compose

Docker-compose is a Docker tool used to create docker containers at scale, it allows you to configure them in one file,<br/>the <i>docker-compose.yml</i> file. 

My <i>docker-compose.yml</i> inside this repository is configured through a Jenkins CICD pipeline using the <i>JenkinsFile</i> script.

The <i>JenkinsFile</i> will run the commands necessary to deploy the docker containers,</br>while the <i>docker-compose.yml<i/> file contains information about what the applications will do.
