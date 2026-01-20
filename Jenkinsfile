pipeline {
    agent any

    environment {
        APP_NAME = "day5-jenkins-credentials"
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo "Checking out source code from GitHub"
                git branch: 'main',
                    url: 'https://github.com/yash1206yernal/jenkins-day2-freestyle.git'
            }
        }

        stage('Build') {
            steps {
                sh '''
                    echo "Starting build..."
                    chmod +x app.sh
                    ./app.sh
                '''
            }
        }

        stage('Use Secret Text Credential') {
            steps {
                withCredentials([
                    string(
                        credentialsId: 'sample-secret',
                        variable: 'MY_SECRET'
                    )
                ]) {
                    sh '''
                        echo "Secret injected securely"
                        echo "Secret length: ${#MY_SECRET}"
                    '''
                }
            }
        }

        stage('Use Username & Password Credential') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'github-creds',
                        usernameVariable: 'GIT_USER',
                        passwordVariable: 'GIT_PASS'
                    )
                ]) {
                    sh '''
                        echo "GitHub username is injected"
                        echo "Username length: ${#GIT_USER}"
                        echo "Password is masked automatically"
                    '''
                }
            }
        }
    }

    post {
        success {
            echo "✅ DAY 5 pipeline executed successfully"
        }
        failure {
            echo "❌ DAY 5 pipeline failed"
        }
        always {
            echo "🧹 Cleaning workspace"
            cleanWs()
        }
    }
}
