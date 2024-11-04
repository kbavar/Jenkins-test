pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the GitHub repository
                git 'https://github.com/kbavar/Jenkins-test.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("hello-world-node")
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Optionally, add commands to run any tests if you have them
                echo 'Tests go here'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Stop any existing container
                    sh 'docker rm -f hello-world-node || true'
                    
                    // Run the new container
                    docker.image("hello-world-node").run("-p 3000:3000 --name hello-world-node")
                }
            }
        }
    }
}
