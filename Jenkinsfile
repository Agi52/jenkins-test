pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
        stage('Test') { 
            steps {
                sh "chmod +x -R /var/jenkins_home/workspace/'latihan pipeline'"
                sh './jenkins/scripts/test.sh' 
            }
        }
        stage('Deploy') {
            steps {
            sh './jenkins/scripts/deliver.sh'
            input message :'Jika sudah berhasil menjalankan klik "Proceed" untuk mengakhiri'
            sh './jenkins/scripts/kill.sh'
        }    
    }
}