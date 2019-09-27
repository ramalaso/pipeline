pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker { image '4514812/ramalaso' }
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