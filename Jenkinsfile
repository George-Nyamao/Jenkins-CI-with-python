pipeline {
	agent {docker {image 'python:3.7.2' } }
	stages {
		stage('build') {
			steps {
				sh 'pip3 install --upgrade pip'
				sh 'python -m pip3 install --user -r requirements.txt'
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