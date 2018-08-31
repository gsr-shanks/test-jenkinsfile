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
                echo 'Provisioning..'
                sh '''ls'''
                echo 'Preparing..'
                sh '''ls'''
                echo 'Testing..'
                sh '''ls'''
                echo 'Analysing..'
                sh '''ls'''
                echo 'Tearing down..'
                sh '''ls'''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
