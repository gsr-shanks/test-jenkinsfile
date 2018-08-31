pipeline {
  agent any
    stages {
        stage("osci-tests") {
            steps {
                sh 'env'
                echo "Initialize..."
            }
        }
        stage("tier-1") {
            parallel {
                stage("system-container-sanity") {
                    steps {
                        echo "system-container-sanity"
                    }
                }
                stage("kcm-sanity") {
                    steps {
                        echo "kcm-sanity"
                    }
                }
            }
        }
        stage("analyse") {
          steps {
            echo "analysing..."
          }
        }
        stage("teardown") {
          steps {
            echo "teardown..."
          }
    }
  }
}
