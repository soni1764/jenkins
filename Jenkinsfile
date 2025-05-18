pipeline {
    agent any  // Run on any available agent

    stages {
        stage('Create First Docker Container and Check OS Version') {
            steps {
                script {
                    echo "Pulling the Alpine Docker image..."
                    sh 'docker pull alpine'

                    echo "Running the first container and checking OS version..."
                    sh 'docker run -d --name container1 alpine tail -f /dev/null'

                    def osVersion1 = sh(script: 'docker exec container1 cat /etc/os-release', returnStdout: true).trim()
                    echo "OS Version inside the first container: ${osVersion1}"

                    sh 'docker stop container1'
                    sh 'docker rm container1'
                }
            }
        }

        stage('Create Second Docker Container and Check OS Version') {
            steps {
                script {
                    echo "Running the second container and checking OS version..."
                    sh 'docker run -d --name container2 alpine tail -f /dev/null'

                    def osVersion2 = sh(script: 'docker exec container2 cat /etc/os-release', returnStdout: true).trim()
                    echo "OS Version inside the second container: ${osVersion2}"

                    sh 'docker stop container2'
                    sh 'docker rm container2'
                }
            }
        }
    }
}
