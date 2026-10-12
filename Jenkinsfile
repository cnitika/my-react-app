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

        stage('Deploy Local') {
            steps {
                sh 'rm -rf /var/www/site/*'
                sh 'cp -r dist/* /var/www/site/'
            }
        }

        stage('Deploy to Remote Server (SSH)') {
            steps {
                sh 'ssh root@remote-server "rm -rf /var/www/html/*"'
                sh 'scp -r dist/* root@remote-server:/var/www/html/'
                sh 'ssh root@remote-server "ls -la /var/www/html"'
            }
        }
    }
}