node {
	stage('scm checkout'){
		def jdk=tool name: 'jdk 8', type: 'jdk'
		git 'https://github.com/jameshsmla/pipelinedemo.git'
	}
	stage('compile and packaging'){
		def mvnHome= tool name: 'M3', type: 'maven'
		bat "mvn package"
	}
}
