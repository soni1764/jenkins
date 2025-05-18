pipeline {
    agent {
        docker {
            image 'docker:24.0.7-cli' // lightweight image with docker CLI
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {
        stage('Check Docker') {
            steps {
                sh 'docker --version'
                sh 'docker ps'
            }
        }
    }
}
