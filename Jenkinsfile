node('master')
{
   stage('ContinuousDownload') 
   {
       git 'https://github.com/konathalabalasrikanth/sai-maven-repo.git'    
   }
   stage('ContinuousBuild')
   {
       sh 'mvn package'
   }
   stage('ContinuousDeployment')
   {
       sh 'scp /home/ubuntu/.jenkins/workspace/grove-pro/webapp/target/webapp.war ubuntu@172.31.24.248:/var/lib/tomcat8/webapps/testapp.war'
   }
   stage('ContinuousTesting')
   {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
       sh 'java -jar /home/ubuntu/.jenkins/workspace/grove-pro/testing.jar'
       
   }
   stage('ContinuousDelivery')
   {
       sh 'scp /home/ubuntu/.jenkins/workspace/grove-pro/webapp/target/webapp.war ubuntu@172.31.11.163:/var/lib/tomcat8/webapps/prodapp.war'
      
   }
   
   
   
}
