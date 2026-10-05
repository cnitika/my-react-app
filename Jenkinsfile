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

        stage('Show Output') {
            steps {
                sh 'ls -la dist'
            }
        }
    }
}