pipeline {
	agent {docker {image 'python:3.7.2' } }
	stages {
		stage('build') {
			steps {
				sh 'sudo -H pip install --upgrade pip'
				sh 'sudo -H pip install -r requirements.txt'
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