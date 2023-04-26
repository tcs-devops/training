pipeline {
    agent any
    tools {
        maven 'm3'
    }

    stages {
        stage('Saludo') {
            steps {
                echo 'Hola amigos'
            }
        }
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/master']], 
                    userRemoteConfigs: [[url: 'https://github.com/jenkins-docs/simple-java-maven-app.git']]
                ])
            }
        }
        stage('Build') {
            steps {
                sh '''ls
                pwd
                mvn clean install
                '''
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Static Analysis'){
            steps {
                bat 'mvn pmd:pmd'
                bat 'mvn checkstyle:checkstyle'
                bat 'mvn findbugs:findbugs'
            }
        }

        stage('Post'){
            steps{
                echo 'Post stage'
            }
            post {
                always {
                    
                    junit 'target/surefire-reports/*.xml'
                    archiveArtifacts artifacts: '**/*.xml'
                    archiveArtifacts artifacts: '**/*.jar'
                }
            }
        }
}
}