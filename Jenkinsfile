pipeline {
  environment {
    registry = "dhfirststep/nodejs_firststep"
    registryCredential = 'doc_hub'
    dockerImage = ''
  }
  agent any
  stages {
    stage('clone repository') {
      steps {
        git 'https://github.com/Jeyakumargd/hw_nodejs.git'
      }
    }
    stage('Build docker image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Docker repo: Push image ') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
            sh 'docker run --rm -d -p 8082:8081 dhfirststep/nodejs_firststep/nodejs_app-20'
          }
        }
      }
    }
       
  }
}

   
