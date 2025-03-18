pipeline {
    agent any

    stages {
        stage('Clone GIT Repo') {
            steps {
                echo 'Cloning code from Github Repo'
				   git branch: 'main', url: 'https://github.com/Cotton677/mindcircuit15d.git'
            }
        }
		
		stage('Build Artifact') {
            steps {
                echo 'Building Artifact using maven build tool'
				   sh 'mvn clean install'
            }
        }
		
		stage('Deploy to Tomcat') {
            steps {
                echo 'Deploying artifact on to Tomcat'
				
				    deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://54.237.130.16:8080/')], contextPath: 'mindpage2', onFailure: false, war: '**/*.war'
            }
        }
    }
}
