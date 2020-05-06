node
{
   
   echo "Jenkins Node name ${env.NODE_NAME}"
def mavenHome = tool name:'maven3.6.3'
stage('CheckoutCode')
{
git branch: 'development', credentialsId: 'a245d093-ae6e-456f-ae0c-ce7a37043d56', url: 'https://github.com/MaryalaHyd/maven-web-application.git'
}

stage('Build')
{
sh "${mavenHome}/bin/mvn clean package"
}

stage('DeployAppToTOmacat')
{
sshagent(['9a699cb9-e1b6-4e1e-93ae-ba86b681c69a']) {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.233.24.168:/opt/apache-tomcat-9.0.34/webapps/"
}
}
}
