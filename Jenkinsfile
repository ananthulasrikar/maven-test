// pipeline {
//   environment {
//     registryCredential = 'dockerhub'
//     dockerImage = ''
//   }
//   agent any
//   stages {
//     stage('Clone repository') {
//       steps {
//         checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [
//           [name: '*/master']
//         ], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [
//           [credentialsId: 'ba8e46a2-d793-4638-8c83-1a153cebe424', url: 'https://github.com/ananthulasrikar/maven-test.git']
//         ]]
//       }
//     }
//     stage('Example Build') {
//       // agent {
//       //   docker {
//       //       image 'maven:3.8.1-adoptopenjdk-11'
//       //       args '-v /Users/srikarananthula/.m2:/root/.m2'
//       //   }
//       // }
//
//       steps {
//         echo 'Hello, Maven'
//         sh 'mvn package'
//       }
//     }
//     stage('Docker build') {
//       // agent { docker 'openjdk:8-jre' }
//       steps {
//         script {
//           dockerImage = docker.build("ananthulasrikar/test")
//         }
//       }
//     }
//     stage('Docker push image') {
//       steps {
//         script {
//           //withDockerRegistry(registry: [credentialsId: ... url: dockerRegistry], toolName: 'docker')
//           withDockerRegistry(registry: [credentialsId: 'dockerhub'], toolName: 'docker') {
//           //docker.withRegistry('', registryCredential) {
//             Image.push('latest')
//           }
//         }
//       }
//     }
//   }
// }



node {
    checkout scm
    def customImage = docker.build("test:${env.BUILD_ID}")
    customImage.push()
}
