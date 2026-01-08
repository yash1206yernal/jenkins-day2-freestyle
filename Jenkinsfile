pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh '''
                  chmod +x app.sh
                  ./app.sh
                '''
            }
        }

        stage('Code Quality') {
            steps {
                script {
                    def scannerHome = tool 'SonarQubeScanner'
                    withSonarQubeEnv('LocalSonar') {
                        sh """
                          ${scannerHome}/bin/sonar-scanner \
                          -Dsonar.projectKey=day4-jenkins \
                          -Dsonar.sources=.
                        """
                    }
                }
            }
        }

    }
}
