pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker { image 'openjdk:11.0.4-jdk' }
            }
            steps{
                sh 'chmod +x gradlew'
                sh './gradlew build'
                sh 'ls -la build/*'
            }
            post{
                always {
                    sh 'ls -ls build/*'
                    junit 'build/test-results/test/*.xml'
                }
            }
		}
	}
}