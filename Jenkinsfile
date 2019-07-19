pipeline {
    
    tools {
        nodejs 'NodeLab'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/YampolskyiVV/mdt'
            }
        }
        stage('Sonarqube') {
            steps {
                // specify server and credentials
                withSonarQubeEnv(installationName: '', credentialsId: 'student19-sonar-token') {
                    script {
                        // install scanner and get installation path
                        def sonarHome = tool 'sonar-scanner-lab'
                        sh """${sonarHome}/bin/sonar-scanner -Dsonar.projectKey=student19-project -Dsonar.sources=www"""
                    }
                }
            }
        }
        stage('Quality gate') {
            steps {
                waitForQualityGate abortPipeline: true
            }
    
}
