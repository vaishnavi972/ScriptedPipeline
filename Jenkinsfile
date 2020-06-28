node('master')
{
    stage('ContinuousDownload') 
    {
      git 'https://github.com/vaishnavi972/maven.git'
    }
    stage('ContinuousBuild') 
    {
      sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment') 
    {
      sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.30.28:/var/lib/tomcat8/webapps/testapp.war'
    }
    stage('ContinuousTesting') 
    {
      git 'https://github.com/vaishnavi972/FunctionalTesting.git'
      sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
      sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.23.102:/var/lib/tomcat8/webapps/prodapp.war'
    }
    
}
