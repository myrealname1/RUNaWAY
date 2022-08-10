pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('eman-dockerhub-token')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t emansal/runaway:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push emansal/runaway:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}