pipeline {
    agent any

    stages {
        stage('Checkout code') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                implementIoBuildStarted()
            }
        }
        stage('Deploy Image') {
                steps {
                    script {
                            log.info("fake deploy")
                            // gcp.updateVMContainer(stableConfig.deployVMName,
                            //         stableConfig.gcpProjectId,
                            //         stableConfig.deployVMZone,
                            //         "${stableConfig.imageRepository}:commit-${env.GIT_COMMIT}",
                            //         ["SPRING_PROFILES_ACTIVE": stableConfig.environment]
                            // )
                    }
                }
                post {
                    always {
                        implementIoBuildEnded
                    }
                }
            }
    }
}
