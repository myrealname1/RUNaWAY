pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('emansal-dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t emansal/RunWay:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push emansal/RunWay:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}