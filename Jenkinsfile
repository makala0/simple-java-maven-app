pipeline {
    agent any
    stages {
        stage('Build') {
            sh 'mvn -B -DskipTests clean package'
        }
    }
    post {
        success {
            jacoco(
                    execPattern: '**/build/jacoco/*.exec',
                    classPattern: '**/build/classes/java/main',
                    sourcePattern: '**/src/main'
            )
        }
    }
}
