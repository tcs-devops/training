//DECLARATIVE PIPELINE
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout ([$class: 'GitSCM',
                          branches: [[name: '*/master' ]],
                          userRemoteConfigs: [[url: 'http://github.com/jenkins-docs/simple-java-maven-app.git']]])
            }
        }
        stage('Build'){
        
      steps{
          sh '''ls 
             pwd
             '''     
      }
        }
        stage('Nombre') {
            steps {
                echo 'Mi nombre es Enrique Guzman'
            }
        }
        stage('Edad') {
            steps {
                echo 'Tengo 25 años'
            }
        }
    }
}
