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
                sh 'docker exec remote-server mkdir -p /var/www/html'
                sh 'docker exec remote-server rm -rf /var/www/html/*'
                sh 'docker cp dist/. remote-server:/var/www/html/'
                echo 'Deployment to remote-server successful!'
            }
        }
    }
}