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
            }
		}
        stage('Unit & Integration Tests') {
            steps {
                script {
                    try {
                        sh './gradlew clean test --no-daemon' //run a gradle task
                    } finally {
                        junit '**/build/test-results/test/*.xml' //make the junit test results available in any case (success & failure)
                    }
                }
            }
        }
	}
}