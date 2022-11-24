FROM jenkins/jenkins:lts
USER root
USER jenkins
RUN jenkins-plugin-cli --plugins "blueocean docker-workflow jacoco htmlpublisher sonar job-dsl maven-plugin pipeline-maven"
