pipeline {
    agent any
    tools {
    maven 'Maven-3.8.6'
    }
    stages {
        stage('Build') {
            steps {
                echo 'TODO: build'
                sh 'mvn clean compile -e'
            }
        }
        stage('Test') {
            steps {
                echo 'TODO: test'
                sh 'mvn clean test -e'
            }
        }
        stage('Package') {
            steps {
                echo 'TODO: package'
                sh 'mvn clean package -e'           
            }
        }
        stage('Sonar') {
            steps {
                 script {      
                withSonarQubeEnv('Sonar') {
                sh 'mvn clean package sonar:sonar'
                   }
                }
            }
        }
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }
    }
}

