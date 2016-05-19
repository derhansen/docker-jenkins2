# Docker and Jenkins 2

Just a simple repository which contains 2 docker buildfiles to setup Jenkins 2 (latest) with a persistent data container

Strongly inspired by https://github.com/Shashikant86/jenkins2-docker/ 

# USAGE
 
## Setup Docker 
 
Clone the repository 
 
         $ git clone https://github.com/derhansen/docker-jenkins2
         $ cd docker-jenkins2
 
Build Images Jenkins Master and Jenkins Data 
  
         $ docker build -t jenkins-data -f dockerfile-jenkinsdata .
         $ docker build -t jenkins2 -f dockerfile-jenkins .

Now launch Containers 
 
         $ docker run --name=jenkins-data jenkins-data
         $ docker run -p 8080:8080 -p 50000:50000 --name=jenkins-master --volumes-from=jenkins-data -d jenkins2
         
Jenkins 2 has now been started on the Docker host on the hosts ip address on port 8080 

## Setup Jenkins

* Open Jenkins 2 by browsing the url ‘http://your-docker-host-ip:8080/‘
 
* Admin Password
Jenkins 2.0 will ask for the Admin password stored in the Jenkins Master container. We can get it and paste it in the console
 
        $ docker exec jenkins-master cat /var/jenkins_home/secrets/initialAdminPassword
 
* User Details
The next step is to fill in the required user details in order to login into the Jenkins.

* Login and have fun
