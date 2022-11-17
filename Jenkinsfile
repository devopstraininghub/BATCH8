pipeline {
    agent any

    stages {
        stage('Clone SCM ') {
            steps {
                echo 'clong project from GH '
				git branch: 'main', credentialsId: 'githubcredentials', url: 'https://github.com/devopstraininghub/BATCH8.git'
				
            }
        }
		
		stage('Build Artifact') {
            steps {
                echo 'building using maven tool'
				sh 'mvn clean install'
        }
		
		}
		stage('Deploy to Tomcat server ') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '7c94969c-a943-4ab0-8c9b-84e52d80cc66', path: '', url: 'http://10.81.10.20:8080')], contextPath: 'FB', war: '**/*.war'
            }
        }
    }
}

