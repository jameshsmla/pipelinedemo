node {
	stage('scm checkout'){
		git 'https://github.com/jameshsmla/pipelinedemo.git'
	}
	stage('compile and packaging'){
		def mvnHome= tool name: 'M3', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
}
