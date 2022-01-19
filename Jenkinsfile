
pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('ddso')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t netsec2minutes/dvwa:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push netsec2minutes/dvwa:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
