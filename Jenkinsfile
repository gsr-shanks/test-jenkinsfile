pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            parallel sanity-file-permissions: {
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
            },
            sanity-initscript: {
            steps {
                echo 'sanity....'
            }
        }
            
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
