pipeline {
	agent any
   tools {
     maven 'Maven'
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
		stage('deploy to tomcat') {
			steps {
				sh 'mvn tomcat9:deploy'
			}
		}
	}
}
