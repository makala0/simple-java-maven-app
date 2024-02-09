pipeline {
    agent any
    try {
        stage('clean') {
            cleanWs()
        }

        stage('checkout') {
            checkout scm
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    } catch (Exception e) {
        throw e
    } finally {
        recordIssues(
                enabledForFailure: true,
                tools: [
                        checkStyle(pattern: '**/target/checkstyle/checkstyle-result/*.xml', reportEncoding: 'UTF-8'),
                ]
        )
    }
}
