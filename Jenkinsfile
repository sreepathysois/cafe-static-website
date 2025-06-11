pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/sreepathysois/cafe-static-website.git'
      }
    }
    stage('Build') {
      steps {
        sh 'docker build -t sreedocker123/cafe-static:v1 .'
      }
    }
    stage('Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
          sh """
          echo "$PASS" | docker login -u "$USER" --password-stdin
          docker push sreedocker123/cafe-static:v1
          """
        }
      }
    }
  }
}
