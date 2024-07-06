node{
   
echo "Job name is: ${env.JOB_NAME}"
echo "Build Number is: ${env.BUILD_NUMBER}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])

def mavenHome = tool name: 'maven3.9.8'

stage('CodeFromGit'){
git branch: 'development', credentialsId: '83169b7c-a253-4884-97ec-ce9d1304a22b', url: 'https://github.com/krisheducation/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}
stage('DeployAppInTomcat'){
sshagent(['bc0ae640-4783-4c52-bede-6c13676b279c']) {
sh 'scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@43.204.109.58:/opt/apache-tomcat-9.0.89/webapps/'
}
}
*/
}
