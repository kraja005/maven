node('master') 
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/balajimanipi/maven.git'
    }
    
    stage('ContinuousBuild') 
    {
        sh label: '', script: 'mvn package'
    
    }
    
    stage('ContinuousDeployment') 
    {
       sh label: '', script: 'scp /root/.jenkins/workspace/Scripted-pipeline/webapp/target/webapp.war root@172.31.44.34:/var/lib/tomcat8/webapps/testenv.war'
    
    }
    
    stage('ContinuousTesting') 
    {
        git 'https://github.com/balajimanipi/FunctionlTesting.git'
        sh label: '', script: 'java -jar testing.jar'
    }
    stage('ContinuousDelivery') 
    {
       input message: 'Waiting for Approval from the DM', ok: 'Approval', submitter: 'ram'
       sh label: '', script: 'scp /root/.jenkins/workspace/Scripted-pipeline/webapp/target/webapp.war root@172.31.45.193:/var/lib/tomcat8/webapps/prodenv.war'
    
    }    
    
    
}
