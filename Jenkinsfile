pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'TODO: build'
                sh './mvnw clean compile -e'
            }
        }
        stage('Sonar') {
            steps {
                 script {      
                withSonarQubeEnv('Sonar') {
                sh "${scannerHome}/bin/sonar-scanner -Dsonar.java.binaries=ejemplo-maven/target/classes -Dsonar.sources=ejemplo-maven/src -Dsonar.projectKey=ejemplo-maven -Dsonar.projectName=ejemplo-maven -Dsonar.projectVersion=${version} -Dsonar.language=java"
                }
                }
            }
        }
        stage('Test') {
            steps {
                echo 'TODO: test'
                sh './mvnw clean test -e'
            }
        }
        stage('Package') {
            steps {
                echo 'TODO: package'
                sh './mvnw clean package -e'           
            }
        }
        stage('Run') {
            steps {
                echo 'TODO: run'
                sh 'nohup bash ./mvnw spring-boot:run &'         
                cleanWs()
            }
        }
    }
}
