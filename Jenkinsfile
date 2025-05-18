pipeline {
    agent any  // Run on any available agent

    stages {
        stage('Create First Docker Container and Check OS Version') {
            steps {
                script {
                    // Pull the Alpine image
                    echo "Pulling the Alpine Docker image..."
                    bat 'docker pull alpine'

                    // Run the first container in detached mode and keep it running
                    echo "Running the first container and checking OS version..."
                    bat 'docker run -d --name container1 alpine tail -f /dev/null'

                    // Get OS version from the first container
                    def osVersion1 = bat(script: 'docker exec container1 cat /etc/os-release', returnStdout: true).trim()
                    
                    // Print the OS version inside the first container
                    echo "OS Version inside the first container: ${osVersion1}"

                    // Clean up the first container
                    bat 'docker stop container1'
                    bat 'docker rm container1'
                }
            }
        }

        stage('Create Second Docker Container and Check OS Version') {
            steps {
                script {
                    // Run the second container in detached mode and keep it running
                    echo "Running the second container and checking OS version..."
                    bat 'docker run -d --name container2 alpine tail -f /dev/null'

                    // Get OS version from the second container
                    def osVersion2 = bat(script: 'docker exec container2 cat /etc/os-release', returnStdout: true).trim()
                    
                    // Print the OS version inside the second container
                    echo "OS Version inside the second container: ${osVersion2}"

                    // Clean up the second container
                    bat 'docker stop container2'
                    bat 'docker rm container2'
                }
            }
        }
    }
}
