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
          docker stop web || true
          docker rm web || true
          docker run -d -p 80:80 --name miniproject
        '''
      }
    }
  }
}
