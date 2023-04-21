pipeline {

  agent any
  
  stages {
   
    stage('Checkout') {
    
      steps {
          checkout ([$class: 'GitSCM',
                     branches: [[name:  '*/jenkins-session' ]],
                     userRemoteConfigs: [[url: 'https://github.com/tcs-devops/training.git' ]]])
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
