node {
    /* Requires the Docker Pipeline plugin to be installed */
	docker.image('ubuntumaven:mvn3.6.0').inside {
    
    // Get Artifactory server instance, defined in the Artifactory Plugin administration page.
    def server = Artifactory.server "jfrog"
    // Create an Artifactory Maven instance.
    def rtMaven = Artifactory.newMavenBuild()
    def buildInfo

    stage('Maven build') {
	sh "mvn  clean compile
    }

     stage('Artifactory configuration') {
        // Tool name from Jenkins configuration
        rtMaven.tool = "mvn"
        // Set Artifactory repositories for dependencies resolution and artifacts deployment.
        rtMaven.deployer releaseRepo:'libs-release-local', snapshotRepo:'libs-snapshot-local', server: server
        rtMaven.resolver releaseRepo:'libs-release', snapshotRepo:'libs-snapshot', server: server
    }
  }
}

   
    
