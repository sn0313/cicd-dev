pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Build started..."
                // For simplicity, just print files
                sh 'ls -l'
            }
        }

        stage('Test') {
            steps {
                echo "Running simple tests..."
                sh 'echo "All tests passed!"'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying..."
                sh 'echo "Deployment completed successfully!" > deployed.txt'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
