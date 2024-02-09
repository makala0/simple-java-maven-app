pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }

    post {
        recordIssues(
                enabledForFailure: true,
                tools: [
                        checkStyle(pattern: '**/target/checkstyle/checkstyle-result/*.xml', reportEncoding: 'UTF-8'),
                ]
        )
    }
}
