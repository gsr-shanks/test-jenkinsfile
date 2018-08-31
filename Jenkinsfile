pipeline {
	agent any
	
	stages {
		stage("Build") {
			steps {
				sh 'mvn -v'
			}
		}
		
		stage("Testing") {
			parallel {
				stage("Unit Tests") {
					agent { docker 'openjdk:7-jdk-alpine' }
					steps {
						sh 'java -version'
					}
				}
				stage("Functional Tests") {
					agent { docker 'openjdk:8-jdk-alpine' }
					steps {
						sh 'java -version'
					}
				}
				stage("Integration Tests") {
					steps {
						sh 'java -version'
					}
				}
			}
		}
		
		stage("Deploy") {
			steps {
				echo "Deploy!"
			}
		}
	}
}


def tasks = [:]

tasks["task_1"] = {
  stage ("task_1"){    
    node('master') {  
        sh 'echo $NODE_NAME'
    }
  }
}
tasks["task_2"] = {
  stage ("task_2"){    
    node('master') {  
        sh 'echo $NODE_NAME'
    }
  }
}

parallel tasks
