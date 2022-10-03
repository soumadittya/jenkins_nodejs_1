pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('jenkins_nodejs_1_docker_hub_key')
        PROJECT_ID = 'subtle-melody-362608'
                CLUSTER_NAME = 'jenkins-pipeline-cluster-1'
                LOCATION = 'us-central1-c'
                CREDENTIALS_ID = 'gke-1'
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t soumadittya/nodeapp:$BUILD_ID .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push soumadittya/nodeapp:$BUILD_ID'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}