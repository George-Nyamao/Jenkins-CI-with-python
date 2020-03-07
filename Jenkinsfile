pipeline {
	agent {docker {image 'python:3.7' } }
	stages {
		stage('build') {
			steps {
				withEnv(["HOME=$env.WORKSPACE"]){
					sh 'pip install -r requirements.txt --proxy="0.0.0.0:9090"'
				}
			}
		}
		stage('test') {
			steps {
				withEnv(["HOME=$env.WORKSPACE"]){
					sh 'python test.py'
				}
			}
			post {
				always {
					junit 'test-reports/*.xml'
				}
			}
		}
	}
}