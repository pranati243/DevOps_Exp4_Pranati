pipeline {
    agent any

    tools {
        maven 'Maven-3.9'
        jdk 'jdk21'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/pranati243/DevOps_Exp4_Pranati.git'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-creds',   // Make sure this matches your Jenkins credentials
                        path: '',
                        url: 'http://127.0.0.1:8081/manager/text'
                    )
                ],
                contextPath: 'my-webapp',
                war: 'target/my-webapp.war'
            }
        }
    }
}
