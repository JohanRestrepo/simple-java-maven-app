pipeline {
    agent any

    stages {
        stage ('Checkout') {
            steps {
                git 'https://github.com/JohanRestrepo/simple-java-maven-app.git'
            }
        }
        stage ('Test') {
            steps {
                sh 'mvn test'
            }
        }
        post {
        always {
            junit 'TestResult.xml'
        }
    }
    }
}