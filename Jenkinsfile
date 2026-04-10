pipeline {
	agent any

	environment {
		DOCKER_IMAGE = 'hello-world-python:latest' //docker image name
	}

	stages {
		stage('checkout') {
			steps {
				git branch: 'main',url: 'https://github.com/404MDB/jenkins_docker_python_hello_world.git'
			}
		}

		stage('Docker Build') {
			steps {
				script {
					if (fileExits('Dockerfile')) {
						sh "docker build -t ${env.Docker_Image} ."
					}
					else {
						error "Dockerfile not found in the workspace. Please create one for your python application."
					}
				}
			}
		}


		stage ('Docker Run (Optional)') {
			steps {
				sh "docker run --rm ${env.DOCKER_IMAGE}"
			}
		}
	}
	
	post {
		success {
			echo 'Success'
		}
		failure {
			echo 'Failure' }
		}
	}
