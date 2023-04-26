pipeline {
	agent any
	
	tools {
		maven 'm3'
	}
	
	stages {
		stage('Checkout') {
			steps{
				checkout([$class: 'GitSCM',
				 branches: [[name: '*/master']],
				 userRemoteConfigs: [[url: 'https://github.com/jenkins-docs/simple-java-maven-app.git']]])
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
		stage('Testing'){
			steps {
				echo 'Results'
			}
		}
		stage('PMD and Findbugs check') {
			steps {
				sh 'mvn clean install pmd:pmd'
				sh 'mvn clean install checkstyle:checkstyle'
				sh 'mvn clean install findbugs:findbugs'
			}
		}
		stage('Reports post') {
			steps {
				echo 'post'
			}
			post {
				always {
					archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
					junit '**/target/surefire-reports/*.xml'
				}
			} 
		}
	}
}
