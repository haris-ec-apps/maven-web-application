node
{
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
    def mavenHome = tool name:"maven3.8.1"
    
    stage('checkOutCode')
    {
        git branch: 'development', credentialsId: 'a3992c14-3324-46ff-a7bc-395960e5c603', url: 'https://github.com/haris-ec-apps/maven-web-application.git'
    }
    stage('Build')
    {
        sh "${mavenHome}/bin/mvn clean package"
    }
  
    /*stage('ExecuteSonarQubeReport')
    {
        sh "${mavenHome}/bin/mvn sonar:sonar"
    }
    stage('UploadArtifactIntoNexus')
    {
        sh "${mavenHome}/bin/mvn deploy"
    }
    stage('DeployAppIntoTomcatServer')
    {
        sshagent(['3684a654-1600-4219-92a9-a08c0bfccd22'])
        {
            sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.235.94.252:/opt/apache-tomcat-9.0.46/webapps/"
        }
    }
    stage('sendEmailNotification')
    {
        mail bcc: 'ahemadsayyed11@gmail.com', body: '''Build over

        Regards,
        Ahmed sayyed''', cc: 'ahemadsayyed11@gmail.com', from: '', replyTo: '', subject: 'Build over..', to: 'ahemadsayyed11@gmail.com'
    }
    */
    
}
