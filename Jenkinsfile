node {
	stage("step 1 git clone") {
	sh echo "clonig code from git"
	
	sh git branch: 'main', url: 'https://github.com/ashwini9921/student-reg-webapp.git'
	
	}
	stage("step 2 build with maven"){
	sh tool name: 'maven', type: 'maven'/bin/mvn clean package
	}
	stage("step 3 verify"){
	sh tool name: 'maven', type: 'maven'/bin/mvn clean verify sonar:sonar
	}
	stage("step 4 deploy"){
	sh deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://18.234.34.165:8080/')], contextPath: null, war: '**/student-reg-webapp*.war'
	}
}
