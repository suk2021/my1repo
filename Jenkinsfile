node {
    /* Requires the Docker Pipeline plugin to be installed */
	docker.image('ubuntu:ans-2.5.01-anssshvim').inside {
    
    // Get Artifactory server instance, defined in the Artifactory Plugin administration page.
    def server = Artifactory.server "jfrog"
    // Create an Artifactory Maven instance.
    def rtMaven = Artifactory.newMavenBuild()
    def buildInfo

    stage('Maven build') {
	sh "mvn  clean compile Dmaven.test.skip=true -Dcheckstyle.skip=true -Dmaven.wagon.http.ssl.insecure=true DaltDeploymentRepository=snapshots::default::http://172.17.0.3:8080/artifactory/repository/libs-snapshots"
    }    
 }
}
