pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Build started..."
                sh 'ls -l'
            }
        }

        stage('Test') {
            steps {
                echo "Running simple tests..."
                sh 'if [ -f index.html ]; then echo "index.html exists, test passed!"; else echo "Test failed!"; exit 1; fi'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to web server..."
                sh 'sudo cp index.html /usr/share/nginx/html/index.html'
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
