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
        stage('Test') {
            parallel linux: {
                node('linux') {
                    checkout scm
                    try {
                        unstash 'app'
                        sh 'make check'
                    }
                    finally {
                        junit '**/target/*.xml'
                    }
                }
            },
            windows: {
                node('windows') {
                    /* .. snip .. */
                }
            }
        }
    }
}
