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
        success {
            jacoco sourcePattern: '**/src/main/java'
        }
    }
}
