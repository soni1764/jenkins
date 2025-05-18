pipeline {
    agent any

    stages {
        stage('Run Node Container and Check Version') {
            steps {
                script {
                    echo "Pulling Node.js Docker image..."
                    bat 'docker pull node:16-alpine'

                    echo "Running Node.js container and checking version..."
                    def nodeVersion = bat(
                        script: 'docker run --rm node:16-alpine node --version',
                        returnStdout: true
                    ).trim()

                    echo "Node.js Version inside container: ${nodeVersion}"
                }
            }
        }
    }
}
