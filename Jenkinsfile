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
        stage('Upload File nexus'){
            steps {
                    nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'my-app', 
                            classifier: '', 
                            file: 'target/my-app-1.0.0.jar', 
                            type: 'jar'
                        ]
                    ], 
                    credentialsId: '982e97b1-c27a-4c1b-a4ba-629976a7660d', 
                    groupId: 'com.mycompany.app', 
                    nexusUrl: 'johanpsl.com:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'JohanPSL', 
                    version: '1.0.0'
            }
        }
        
    }
    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
    }
    