pipeline {
	agent any

	tools {
		maven 'Maven 3.9.5'
		jdk 'JDK 21'
	}

	stages {
		stage('Checkout') {
			steps {
				echo 'Checking out code...'
				git branch: 'main',
				credentialsId: 'git-ssh-key',
				url: 'git@github.com:Thisbean/demo.git'
			}
		}

		stage('Build') {
			steps {
				echo 'Building application...'
				bat '''
                cd demo
                mvnw.cmd clean package -DskipTests
                '''
			}
		}

		stage('Test') {
			steps {
				echo 'Running tests...'
				bat '''
                cd demo
                mvnw.cmd test
                '''
			}
		}
	}
}