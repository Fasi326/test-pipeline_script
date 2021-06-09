node

{
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('*/1 * * * *')])])
    
    def mavenHome = tool name:"maven3.8.1"

    stage('git checkout')
    {
     git credentialsId: '02f79dd1-790d-4d7c-8317-98a004fcabb8', url: 'https://github.com/Fasi326/maven-web-application.git'   
        
    }
    
    stage('building package')
    {
        
        sh  " ${mavenHome}/bin/mvn clean package " 
    }
    
    //checking poll scm
    
    /*stage('generating report')
    {
        
        sh  " ${mavenHome}/bin/mvn sonar:sonar " 
    }
    
     stage('storing Artifact')
    {
        
        sh  " ${mavenHome}/bin/mvn deploy " 
    }
    
    
    stage('deploying')
    {
        sshagent(['122af1f3-1ffe-4d16-909e-47a483fa89eb']) 
        {
        
         sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@52.66.83.171:/opt/apache-tomcat-9.0.45/webapps/"
        }    
    }*/
    
    stage('notification mail')
    {
        mail bcc: '', body: 'Please check the job and verify', cc: 'rehamanyasin@gmail.com', from: '', replyTo: '', subject: 'Build status completed', to: 'fasirehaman@gmail.com'
    }
    
}
