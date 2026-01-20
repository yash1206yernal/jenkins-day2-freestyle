pipeline {
    agent any

    environment {
        GIT_CREDS = credentials('github-creds')
    }

    stages {

        stage('Checkout Repo') {
            steps {
                sh '''
                    echo "Cloning repository using secure credentials"
                    git clone https://${GIT_CREDS_USR}:${GIT_CREDS_PSW}@github.com/yash1206yernal/jenkins-day2-freestyle.git
                '''
            }
        }

        stage('Verify Code') {
            steps {
                sh '''
                    echo "Listing files:"
                    ls -l jenkins-day2-freestyle
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    cd jenkins-day2-freestyle
                    chmod +x app.sh
                    ./app.sh
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
        always {
            cleanWs()
        }
    }
}
