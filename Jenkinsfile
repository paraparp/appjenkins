pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app:test .'
      }
    }
    stage('Test') {
      steps {
        echo 'Test'
        sh 'docker run app'
        sh 'docker stop app'
    }
      }
    stage('Push Registry') {
      steps {
        sh 'docker tag app dobarqueiro/app:stable'
        sh 'docker push  dobarqueiro/app:stable'
      }
    }

}
}
