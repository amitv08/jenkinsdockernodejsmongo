# jenkinsdockernodejsmongo
Jenkins, Docker, Nodejs, Mongo db


One of the important step is to create dockerised jenkins 

Step1 install docker 
step2: load jenkins image in docker 
      mkdir -p /var/jenkins_home
      chown -R 1000:1000 /var/jenkins_home/
      docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -d --name jenkins jenkins/jenkins
step3: Launch jenkins from browser with port 8080 as mentioned above. and login with initial password present in more /var/jenkins_home/secrets/initialAdminPassword
step4: install the default plugins
step5: (Optional) if you dont configure the users and want to use admin make the flag false in config file
step5: now stop the jenkins running in docker
      docker stop jenkins
      docker rm jenkins
step6: Now build DockeredJenkins image using docker build -t jenkins-docker Dockerfile-Jenkins
step7: change permissions of /var/run/docker.sock file as sudo chmod 777 /var/run/docker.sock 
step8: Run the newly built docker image as 
      docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock --name jenkins -d jenkins-docker -u docker
step9: Try login to jenkins using 
          docker exec -it jenkins bash
       and then run 
          docker ps -a 
       if this works success then your dockered jenkins is success.
 Step10: proceed with your build.
