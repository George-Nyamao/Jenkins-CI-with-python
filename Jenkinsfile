pipeline {
  agent { docker { image 'python:3.7.6' } }
  stages {
    stage('build') {
      steps {
        sh 'pip3 install -r requirements.txt --proxy="tcp://0.0.0.0:2376"'
      }
    }
    stage('test') {
      steps {
        sh 'python test.py'
      }   
    }
  }
}
