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
        script {
            def scannerHome = tool 'sonar-scanner'
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

