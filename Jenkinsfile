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
					agent { 'any' }
					steps {
						sh 'java -version'
					}
				}
				stage("Functional Tests") {
					agent { 'any' }
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
