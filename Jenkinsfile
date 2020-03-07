pipeline {
	agent {docker {image 'python:3.7' } }
	stages {
		stage('build') {
			steps {
				withEnv(["HOME=$env.WORKSPACE"]){
					sh 'pip3 install --trusted-host pypi.python.org -r requirements.txt'
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