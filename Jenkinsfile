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
                // Debugging: List files to ensure paths exist
                sh "ls -l ${env.WORKSPACE}"
                
                // Update permissions (if necessary)
                sh "chmod +x -R ${env.WORKSPACE}/latihan"
                
                // Run the test script
                sh './jenkins/scripts/test.sh' 
            }
        }    
    }
}