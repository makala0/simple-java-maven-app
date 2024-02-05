node {
    properties([buildDiscarder(logRotator(artifactNumToKeepStr: '10', numToKeepStr: '60'))])

    timestamps {
        try {
            stage('clean') {
                cleanWs()
            }

            stage('checkout') {
                checkout scm
            }

            stage('build') {
                timeout(time: 4, unit: 'HOURS') {
                    def buildEnv = docker.build(
                            'build-env:snapshot',
                            ' --build-arg USER_ID=$(id -u)' +
                                    ' --build-arg GROUP_ID=$(id -g)' +
                                    ' --build-arg USER_NAME=$USER' +
                                    ' .')

                }
            }
        } catch (Exception e) {
            throw e
        } finally {
            recordIssues(
                    enabledForFailure: true,
                    tools: [
                            java(reportEncoding: 'UTF-8'),
                            kotlin(reportEncoding: 'UTF-8'),
                            pmdParser(pattern: '**/build/reports/pmd/*.xml', reportEncoding: 'UTF-8'),
                            checkStyle(pattern: '**/build/reports/checkstyle/*.xml', reportEncoding: 'UTF-8'),
                            spotBugs(pattern: '**/build/reports/spotbugs/*.xml', reportEncoding: 'UTF-8', useRankAsPriority: true),
                            detekt(pattern: '**/build/reports/detekt/*.xml', reportEncoding: 'UTF-8'),
                            junitParser(pattern: '**/build/test-results/test/*.xml', reportEncoding: 'UTF-8')
                    ]
            )

            jacoco sourcePattern: '**/src/main/java, **src/main/kotlin'
            junit skipPublishingChecks: true, testResults: '**/build/test-results/test/*.xml'
        }
    }
}