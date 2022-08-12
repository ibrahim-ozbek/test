pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-ibrahim')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t eaglehaslanded/app:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push eaglehaslanded/app:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}