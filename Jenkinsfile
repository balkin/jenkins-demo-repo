pipeline {
    agent any

    stages {
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
            echo "Always"
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
