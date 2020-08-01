pipeline {
    agent any

    stages {
        stage ('Checkout') {
            steps {
                git 'https://github.com/JohanRestrepo/simple-java-maven-app.git'
            }
        }
    }

    stages {
        stage ('Test') {
            steps {
                junit 'pom.xml'
            }
        }
    }
}
