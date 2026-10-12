pipeline {
    agent any

    tools {
        nodejs 'node24'
    }

    stages {
        stage('Check Tools') {
            steps {
                sh 'node --version'
                sh 'npm --version'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy to Remote Server') {
            steps {
                echo 'Copying build files to remote-server container...'
                
                // Ensure target directory exists in remote server
                sh 'docker exec remote-server mkdir -p /var/www/html'
                
                // Clean old files on remote server
                sh 'docker exec remote-server rm -rf /var/www/html/*'
                
                // Copy built dist files from Jenkins workspace to remote-server container
                sh 'docker cp dist/. remote-server:/var/www/html/'
                
                echo 'Deployment to remote-server successful!'
            }
        }
    }
}