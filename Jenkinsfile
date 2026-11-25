pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('Build ...') {
            steps {
                echo '---build started---'
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo '---build completed---'
            }
        }
        stage('Test ...') {
            steps {
                echo '---test started---'
                sh 'mvn surefire-report:report'
                echo '---test completed---'
            }
        }
        stage('SonarQubeAnalysis') {
            environment {
                scannerHome = tool 'SQ_Scanner'
            }
            steps {
                withSonarQubeEnv('SQ_Server'){
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
