pipeline {
	agent {docker {image 'python:3.7.2' } }
	stages {
		stage('build') {
			steps {
				sh 'pip3 install --trusted-host pypi.python.org -r requirements.txt'
			}
		}
		stage('test') {
			steps {
				sh 'python test.py'
			}
			post {
				always {
					junit 'test-reports/*.xml'
				}
			}
		}
	}
}