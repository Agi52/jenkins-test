pipeline {
    agent {
        docker {
    image 'node:lts-buster-slim'
    args '-p 3000:3000 --network host -v /var/run/docker.sock:/var/run/docker.sock'
}
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the website? (Click "Proceed" to continue)'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs!'
        }
    }
}
