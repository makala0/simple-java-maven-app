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
        }
    }
}
