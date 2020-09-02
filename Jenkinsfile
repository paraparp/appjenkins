pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app:test .'
      }
    }

    stage('Push Registry') {
      steps {


withCredentials([usernamePassword(credentialsId: 'docker_hub_login', passwordVariable: 'password', usernameVariable: 'user')]) {

echo '$password'
echo '$user'
          sh 'docker login -u $user -p $password'
          sh 'docker tag app:test dobarqueiro/app:stable'
     sh 'docker push  dobarqueiro/app:stable'
        }


      }
    }

}
}
