pipeline {
	agent any
	// agent {docker {image 'maven:3.6.3'}}

	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Path - $path"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "NODE_NAME - $env.NODE_NAME"
				echo "JOB_BASE_NAME - $env.JOB_BASE_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
				echo "Build"
			}
		}

		stage('Compile') {
			steps{
				sh "mvn clean compile"
			}

		}
		stage('Test') {
			steps {
				sh "mvn test"
			}
		}
		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}		
		}
		
		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}		
		}
		
		stage("Build Docker Image") {
			steps {
				// dockerbuild -t dconroy1971/currency-exchange-devops:$env.BUILD_TAG
				script{
					dockerImage = docker.build("dconroy1971/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage("Push Docker Image") {
			steps {
				// docker push dconroy1971/currency-exchange-devops:$env.BUILD_TAG
				script{
					docker.withRegistry('', 'dockerhub') {
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}
		}
	} 
	post{
		always {
			echo 'Im awesome. I run Always'
		}
		success {
			echo 'Success'
		}
		failure {
			echo 'Something went wrong'
		}
	}
}