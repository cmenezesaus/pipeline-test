pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage('Echo') {
      steps {
        sh 'echo "Hello World"'
      }
    }
    // stage('Build') {
    //   steps {
    //     sh 'docker build -t cmenezesaus/cmenezesaus/gitops .'
    //   }
    // }
    // stage('Login') {
    //   steps {
    //     sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
    //   }
    // }
    // stage('Push') {
    //   steps {
    //     sh 'docker push cmenezesaus/gitops'
    //   }
    // }
  }
  // post {
  //   always {
  //     sh 'docker logout'
  //   }
  // }
}