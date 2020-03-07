pipeline {
	agent {docker {image 'python:3.7' } }
	stages {
		stage('build') {
			steps {
				withEnv(["HOME=$env.WORKSPACE"]){
					sh 'pip install -r requirements.txt --proxy="docker:8080"'
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