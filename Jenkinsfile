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

        stage('Deploy') {
            steps {
                sh 'rm -rf /var/www/site/*'
                sh 'cp -r dist/* /var/www/site/'
                sh 'ls -la /var/www/site'
            }
        }
    }
}