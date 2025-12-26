pipeline {
  agent any

  stages {

    stage('Clone') {
      steps {
        checkout scm
      }
    }

    stage('Build Image') {
      steps {
        sh 'docker build -t miniproject .'
      }
    }

    stage('Deploy') {
      steps {
        sh '''
          docker stop miniproject || true
          docker rm miniproject || true
          docker run -d -p 80:80 --name miniproject miniproject
        '''
      }
    }

  }
}
