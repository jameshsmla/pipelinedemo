node {
	stage('scm checkout'){
		git 'https://github.com/jameshsmla/pipelinedemo.git'
	}
	stage('compile and packaging'){
		def jdkpath=tool name: 'JAVA_HOME', type: 'jdk'
		def mvnHome= tool name: 'M3', type: 'maven'
		echo '-------------start version information ---------'
		bat "mvn package"
	}
	stage('Sonar analysi'){
	def sonarreport=tool name: 'SonarQuebe', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
	def mvnHome= tool name: 'M3', type: 'maven'
	withSonarQubeEnv('sonar') { // If you have configured more than one global server connection, you can specify its name
      bat "${mvnHome}/bin/mvn sonar:sonar"
	
	}
	}
}
