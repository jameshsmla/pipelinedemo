node {
	stage('scm checkout'){
		git ''
	}
	stage('compile and packaging'){
		def mvnHome= tool name: 'maven-3', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
}