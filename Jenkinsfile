pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
			}		
		}
	} 
	post{
		always {
			echo 'Im awesome. I run Always'
		}
		success {
			echo ' on success'
		}
		failure {
			echo ' on fail'
		}
	}
}