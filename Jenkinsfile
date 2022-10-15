pipeline {
	// agent {docker {image 'maven:3.6.3'}}
	stages {
		stage('Build') {
			steps {
				// sh 'mvn --version'
				echo "$path"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD.TAG - $env.BUILD.TAG"
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