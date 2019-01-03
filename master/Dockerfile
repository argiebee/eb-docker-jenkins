# Starting off with the Jenkins base Image
FROM jenkins/jenkins:latest
 
# Installing the plugins we need using the in-built install-plugins.sh script
RUN /usr/local/bin/install-plugins.sh git matrix-auth workflow-aggregator docker-workflow blueocean credentials-binding mstest pipeline-utility-steps jdk-tool command-agent-launcher amazon-web-services-sdk aws-elastic-beanstalk-deployment bouncycastle-api cloudbees-aws-credentials pipeline-utility-steps
 
# Setting up environment variables for Jenkins admin user
ENV JENKINS_USER admin
ENV JENKINS_PASS J3nk1n5
 
# Skip the initial setup wizard
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
 
# Start-up scripts to set number of executors and creating the admin user
COPY executors.groovy /usr/share/jenkins/ref/init.groovy.d/
COPY default-user.groovy /usr/share/jenkins/ref/init.groovy.d/
COPY jobs/eb-docker-nginx-proxy/config.xml /usr/share/jenkins/ref/jobs/eb-docker-nginx-proxy/
 
VOLUME /var/jenkins_home