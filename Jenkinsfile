pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Kimiollie/testDocker.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test & Coverage') {
            steps {
                sh 'mvn test jacoco:report'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                    jacoco(execPattern: 'target/jacoco.exec')
                }
            }
        }
    }
}
