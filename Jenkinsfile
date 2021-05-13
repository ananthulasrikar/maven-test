pipeline {
  environment {
    imagename = "ananthulasrikar/test"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git([url: 'https://github.com/ananthulasrikar/maven-test.git', branch: 'master', credentialsId: 'ba8e46a2-d793-4638-8c83-1a153cebe424'])
      }
    }
    stage('Building image') {
      steps {
        script {
          dockerImage = docker.build imagename
        }
      }
    }
    stage('Deploy Image') {
      steps {
        script {
          docker.withRegistry('', registryCredential) {
            dockerImage.push('latest')
          }
        }
      }
    }
  }
}
