pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building dev branch..."
                sh 'ls -l'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'if [ -f index.html ]; then echo "Test passed"; else exit 1; fi'
            }
        }

        stage('Promote to Prod') {
            when {
                branch 'main' // Only mirror if main branch passes
            }
            steps {
                echo "Mirroring code to production repo..."
                withCredentials([usernamePassword(credentialsId: 'github-creds', usernameVariable: 'USER', passwordVariable: 'TOKEN')]) {
                    sh '''
                    git config --global user.email "jenkins@myci.com"
                    git config --global user.name "Jenkins CI"
                    git remote add prod https://${USER}:${TOKEN}@github.com/sn0313/cicd-prod.git || true
                    git push prod main --force
                    '''
                }
            }
        }
    }

    post {
        success { echo "CI Pipeline succeeded and mirrored to prod." }
        failure { echo "CI Pipeline failed." }
    }
}

