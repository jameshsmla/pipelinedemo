node {
	stage('scm checkout'){
		tool name: 'JAVA_HOME', type: 'jdk'
		git 'https://github.com/jameshsmla/pipelinedemo.git'
	}
	stage('compile and packaging'){
		def mvnHome= tool name: 'M3', type: 'maven'
		echo '-------------start version information ---------'
		bat "mvn package"
	}
}
