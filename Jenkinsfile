pipeline {
agent any
stages {
stage('Source') {
steps {
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/jameshsmla/pipelinedemo.git']]])
}
}
stage('Build') {
tools {
jdk 'JDK8'
maven 'Maven3'
}
steps {
powershell 'java -version'
powershell 'mvn -version'
powershell 'mvn clean package'
archiveArtifacts 'target/*.war'
}
  }
stage ('sonar Analysis'){
tools {
jdk 'JDK8'
maven 'Maven3'
}
steps{
withSonarQubeEnv(installationName: 'sonar'){
bat label: '', script: 'mvn sonar:sonar'
}
}
}
  stage('Approval') {
            steps {
                script {
                    def deploymentDelay = input id: 'Deploy', message: 'Deploy to production?', submitter: 'Lavanya,admin'
                 
                }
            }
        }
  //With Delay Option in Approval
  // stage('Approval') {
            //        steps {
              //  script {
               //     def deploymentDelay = input id: 'Deploy', message: 'Deploy to production?', submitter: 'rkivisto,admin', parameters: [choice(choices: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18', '19', '20', '21', '22', '23', '24'], description: 'Hours to delay deployment?', name: 'deploymentDelay')]
                //    sleep time: deploymentDelay.toInteger(), unit: 'HOURS'
               // }
         //   }
      //  }
stage('Deploy') {
steps{
echo "Deploying"
deploy adapters: [tomcat7(credentialsId: 'tomcat', path: '', url: 'http://localhost:8085/')], contextPath: 'happytrip', war: '**/*.war'
}
}
 
  stage('Email Notification'){
    steps{
    mail bcc: '', body: '''hi,
  Email Notification for Happytrip
Thanks,
Lavanya Jami''', cc: '', from: '', replyTo: '', subject: 'Email Notification', to: 'lavanyajami.pratian@gmail.com'
   
    }
  }
}
}