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
        stage('Build Jar'){
        steps {
            sh 'mvn package'
            stash includes: 'target/*.jar', name: 'targetfiles'
        }
    }  
    }
    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
    }
    