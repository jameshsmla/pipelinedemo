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
              echo 'Building stage'
              sh 'mvn --version'
            }
        }
   }
}