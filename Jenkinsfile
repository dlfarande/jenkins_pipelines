pipeline {
  environment {
    registry = "dlfarande/devops_pipeline_jenkins"
    registryCredential = 'dockerhubcredentials'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Checkout') 
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

