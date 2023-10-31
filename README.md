# docker-compose

Docker-compose is a Docker tool used to create docker containers at scale, it allows you to configure them in one file,<br/>the <i>docker-compose.yml</i> file. 

My <i>docker-compose.yml</i> (written in yaml) inside this repository is configured through a Jenkins CICD pipeline using the <i>JenkinsFile</i> script.

The <i>JenkinsFile</i> will run the commands necessary to deploy the docker containers,</br>while the <i>docker-compose.yml</i> file contains information about what the applications will do.

<hr/>

The docker-compose file deploys an echo-server that takes a request seny by a client (in this case, us) & returns it.
<br/>The file also maps the ports (requesting port 3000 will map to port 80 on the docker container)<nr/>
The container image URI is:

```
ealen/echo-server:latest
```

The echo-server will take a client request & send it back to the client, we will format this request later on.

<hr/>

I will explain the <i>JenkinsFile</i> Build steps:

  - <b>Git Checkout:</b> This will clone this current repo that contains the docker-compose.yml file using Git plugin within Jenkins.
  - <b>Verify Tooling:</b> This will verify that the machine has the necessary tools (packages) to run Docker-compose and run the applications.</br>
     (Docker for containerizing, docker-compose for multi-container running, curl to return output, jq to parse output into JSON format)
  - <b>Start Container:</b> This deploys the docker-compose file by using ssh to connect to the machine & deploying the container on the machine<br/>
    The 'docker-compose up' command runs the entire <i>docker-compose.yml</i> file from the machine you are using
  - <b>Run tests against the container:</b> Run the curl command with jq format processor to output echo server

<hr/>

Jenkins Ouput console will output something like: 

<img width="424" alt="image" src="https://github.com/Semir-Devops/docker-compose/assets/144611511/e5b79aae-ee69-4e40-99ad-2cc0ca0b8674">

