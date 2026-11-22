pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('git clone') {
            steps {
                git url : 'https://github.com/9kaus/java_war_practice.git', branch : 'main'
            }
        }
        stage('Build ...') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}

