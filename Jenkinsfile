pipeline {
    agent any
  stages {
    stage('Checkout') {
      steps {
        git credentialsId: 'githubcredentials', url: 'https://github.com'
      }
    }
    stage('Docker Build') {
      steps{
        script {
          dockerImage = docker.build registry + ":latests-$BUILD_NUMBER"
        }
      }
    }
    stage('Docker Push') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
           dockerImage.push()
          }
        }
      }
    }
  }
}

