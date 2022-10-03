pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('jenkins_nodejs_1_docker_hub_key')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t soumadittya/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push bharathirajatut/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}