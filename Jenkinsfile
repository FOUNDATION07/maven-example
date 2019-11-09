pipeline {
    agent any 
    stages {
        stage('Code Checkout') { 
            steps {
                sh 'echo code checkout'
                git credentialsId: 'githubID', url: 'https://github.com/itrainpulsars/maven-example.git'
            }
        }
        stage('Build') { 
            steps {
              withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn clean compile'
             } 
            }
        }
        stage('Test') { 
            steps {
               withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn test'
             }  
            }
        }
         stage('code analysis') { 
            steps {
               withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh mvn sonar:sonar \
                  -Dsonar.projectKey=maven-example-1 \
                  -Dsonar.organization=foundation-07 \
                  -Dsonar.host.url=https://sonarcloud.io \
                  -Dsonar.login=59e9983a58d8ce6838491dcc805247954fcc777e'
             }  
            }
        }
        
        stage('Package') { 
            steps {
                withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn package'
             }  
            }
        }
        stage('Docker Image') { 
            steps {
                sh 'echo Docker Image' 
            }
        }
        stage('Deploy to Dev') { 
            steps {
                sh 'echo Deploy to Dev' 
            }
        }
        stage('Deploy to Prod') { 
            steps {
                sh 'echo Deploy to Prod' 
            }
        }
    }
}
