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
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }


    post {
        // Always runs. And it runs before any of the other post conditions.
        always {
            echo "Always0"
            implementIoBuildEnded
            echo "Always1"
        }
        success {
            echo "Success"
        }
        unstable {
            echo "Unstable"
        }
        failure {
            echo "Failed"
        }
    }
}
