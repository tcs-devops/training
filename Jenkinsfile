pipeline {

  agent any
  
  tools{
    maven 'm3'
  }
  
  stages {
    
    stage('Saludo') {
      
      steps {
      echo 'Hola amigos'
      } 
    }
    
    stage('Nombre') {
      
      steps {
      echo 'Mi nombre es Enrique'
      } 
    }
    
    stage('Edad') {
      
      steps {
      echo 'Tengo 24 años'
      } 
    }
   
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
            mvn clean install
             '''     
      }
    }
  }
}
