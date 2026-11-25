pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('Build ...') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('SonarQubeAnalysis') {
            environment {
                scannerHome = tool 'SQ_Scanner'
            }
            steps {
                withSonarQubeEnv('SQ_Server'){
                    sh "${scannerHome}/bin/Sonar-Scanner"
                }
            }
        }
    }
}
