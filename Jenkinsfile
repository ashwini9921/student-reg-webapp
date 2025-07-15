pipeline {
	agent any

	tools {
		maven 'Maven 3.9.10'
	}

	stages {
		stage('Build') {
			steps {
				sh 'mvn clean package'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage('Deploy') {
			when {
				expression { env.BRANCH_NAME == 'pipelineonVM' }
			}
			steps {
				sh 'mvn deploy'
			}
		}
	}
}
