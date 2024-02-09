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
        success {
            checkStyle(pattern: '**/target/checkstyle/checkstyle-result/*.xml', reportEncoding: 'UTF-8')
//            checkStyle(pattern: '**/build/reports/checkstyle/*.xml', reportEncoding: 'UTF-8')
//            spotBugs(pattern: '**/build/reports/spotbugs/*.xml', reportEncoding: 'UTF-8', useRankAsPriority: true)
//            detekt(pattern: '**/build/reports/detekt/*.xml', reportEncoding: 'UTF-8')
        }
    }
}
