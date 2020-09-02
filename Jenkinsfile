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
    

withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh 'docker login -u $dockerHubUser -p $dockerHubPassword'
          sh 'docker tag jenkins jenkins:stable'
          sh 'docker push xxxxxx/jenkins:stable'
        }


      }
    }

}
}
