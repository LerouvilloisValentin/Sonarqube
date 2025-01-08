pipeline {
    agent any
    
    tools {
        maven 'Maven 3.9.9'
    }
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/LerouvilloisValentin/Sonarqube.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
