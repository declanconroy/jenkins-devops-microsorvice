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
			echo 'run on success'
		}
		failure {
			echo 'run on fail'
		}
	}
}