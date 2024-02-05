pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
    post {
        recordIssues {
            jacoco sourcePattern: '**/src/main/java'
        }
    }
}
