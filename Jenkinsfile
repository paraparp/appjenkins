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
        sh 'docker run -d name app app:test'
        sh 'nc -vz localhost 81'
        sh 'docker stop app'
    }
      }
    stage('Push Registry') {
      steps {


withCredentials([usernamePassword(credentialsId: 'docker_hub_login', passwordVariable: 'password', usernameVariable: 'user')]) {
          sh 'docker login -u $user -p $password'
          sh 'docker tag app:test dobarqueiro/app:stable'
     sh 'docker push  dobarqueiro/app:stable'
        }


      }
    }

}
}
