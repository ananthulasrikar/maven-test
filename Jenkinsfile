pipeline {
  agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'ba8e46a2-d793-4638-8c83-1a153cebe424', url: 'https://github.com/ananthulasrikar/maven-test.git']]]
            }
        }

        stage('Example Build') {
            agent { docker 'maven:3.8.1-openjdk-11' }
            steps {
                echo 'Hello, Maven'
                sh 'mvn package'
            }
        }
        // stage('Docker build') {
        //     // agent { docker 'openjdk:8-jre' }
        //     steps {
        //         docker.build("ananthulasrikar/test")
        //     }
        // }
        //
        // stage('Docker push image') {
        //     steps {
        //        docker.withRegistry('', 'dockerhub') {
        //            app.push()
        //        }
        //     }
        // }
    }
}
