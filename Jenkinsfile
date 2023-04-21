pipeline {

  agent any
  
  stages {
   
    stage('Checkout') {
    
      steps {
          checkout ([$class: 'GitSCM',
                     branches: [[name:  '*/master' ]],
                     userRemoteConfigs: [[url: 'https://github.com/jenkins-docs/simple-java-maven-app.git' ]]])
      }    
    }
    stage('Build'){
        
      steps{
          sh '''ls 
             pwd
             '''     
      }
    }
  }
}
