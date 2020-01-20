node {
	stage('scm checkout'){
		git 'https://github.com/jameshsmla/pipelinedemo.git'
	}
	stage('compile and packaging'){
		def jdkpath=tool name: 'JAVA_HOME', type: 'jdk'
		def mvnHome= tool name: 'M3', type: 'maven'
		echo '-------------start version information ---------'
		bat "mvn install"
	}
	stage('Sonar analysis'){
		def sonarreport=tool name: 'SonarQuebe', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
		def mvnHome= tool name: 'M3', type: 'maven'
		withSonarQubeEnv('sonar') { 
	      bat "mvn sonar:sonar"
		
		}
		
	}
	stage ('running app'){
	bat "mvn install"
	}
}
