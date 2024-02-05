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
//            jacoco sourcePattern: '**/src/main/java'
//            checkStyle(pattern: '**/build/reports/checkstyle/*.xml', reportEncoding: 'UTF-8')
//            spotBugs(pattern: '**/build/reports/spotbugs/*.xml', reportEncoding: 'UTF-8', useRankAsPriority: true)
//            detekt(pattern: '**/build/reports/detekt/*.xml', reportEncoding: 'UTF-8')
        }
    }
}
