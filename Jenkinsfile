pipeline {
    agent any
    
    tools {
        maven 'Maven 3.9.8'
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
        
        stage('SonarQube Analysis') {
            steps {
                script {
                    def mvnHome = tool 'Maven 3.9.8'
                    withSonarQubeEnv('SonarQ') {
                        sh '''
                            ${mvnHome}/bin/mvn clean verify sonar:sonar \
                            -Dsonar.projectKey=Vulnado \
                            -Dsonar.projectName=Vulnado
                        '''
                    }
                }
            }
        }
    }
}
