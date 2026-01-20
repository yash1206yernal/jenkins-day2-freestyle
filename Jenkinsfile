pipeline {
    agent any

    environment {
        GIT_CREDS = credentials('github-creds')
    }

    stages {

        stage('Checkout Private Repo') {
            steps {
                sh '''
                    echo "Cloning private repo using environment credentials"
                    git clone https://${GIT_CREDS_USR}:${GIT_CREDS_PSW}@github.com/yash1206yernal/private-repo.git
                '''
            }
        }

        stage('Verify Code') {
            steps {
                sh '''
                    echo "Files inside repo:"
                    ls -l private-repo
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    echo "Simulating build step"
                    echo "Build successful"
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Day 5 – Part 5 completed successfully"
        }
        failure {
            echo "❌ Build failed"
        }
    }
}
