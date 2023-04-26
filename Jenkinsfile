pipeline {
    agent any
    tools {
        maven 'm3'
        maven 'pmd:pmd'
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
                sh 'mvn pmd:pmd'
                sh 'mvn checkstyle:checkstyle'
                sh 'mvn findbugs:findbugs'
                recordIssues(tools: [checkStyle(pattern: 'target/checkstyle-result.xml'), pmdParser(pattern: 'target/pmd.xml'), findBugs(pattern: 'target/findbugsXml.xml',useRankAsPriority:true)])
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