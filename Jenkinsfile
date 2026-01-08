pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'chmod +x app.sh'
                sh './app.sh'
            }
        }

        stage('Code Quality') {
            steps {
                withSonarQubeEnv('LocalSonar') {
                    sh """
                      sonar-scanner \
                      -Dsonar.projectKey=day4-jenkins \
                      -Dsonar.sources=.
                    """
                }
            }
        }
    }
}
