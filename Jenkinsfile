pipeline {
   agent any

      stages {
          stage('Check out SCM') {
             steps {
                echo 'hello world'
                git('https://github.com/jameshsmla/pipelinedemo.git')
         }
      }
      stage('build') {
            steps {
            def mvnHome=tool name: 'M3', type: 'maven'
              echo 'Building stage'
              sh "${mvnHome}/bin/mvn package"
            }
        }
   }
}