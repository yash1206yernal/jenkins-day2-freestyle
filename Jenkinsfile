pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code checkout handled by Jenkins'
            }
        }

        stage('Build') {
            steps {
                echo 'Running build stage'
                sh 'chmod +x app.sh'
                sh './app.sh'
            }
        }
    }
}
