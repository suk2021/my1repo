pipeline {
    agent {
        docker {
            image 'ubuntumaven:mvn3.6.0'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }    
    }
}
