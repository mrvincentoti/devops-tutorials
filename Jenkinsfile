pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-hub-credentials')
	}

	stages {

		stage('Build') {

			steps {
				sh 'sudo docker build -t voti/devopsapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'sudo docker push voti/devopsapp:latest'
			}
		}
	}

	post {
		always {
			sh 'sudo docker logout'
		}
	}

}