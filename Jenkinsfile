pipeline {
	agent any
	
	stages {
		stage("Build") {
			steps {
				sh 'java -version'
			}
		}
		
		stage("Testing") {
			parallel {
				stage("Unit Tests") {
					steps {
						sh 'java -version'
					}
				}
				stage("Functional Tests") {
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
