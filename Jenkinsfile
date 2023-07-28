pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        script{
                def mvnHome = tool name: 'Maven', type: 'maven'
                sh "${mvnHome}/bin/mvn package"
        }
      }
    }
    stage('Building Docker Image') {
      steps{
        script {
          sh "docker build -t deepakramanan/cicd-poc-docker-jenkins-ansible:$BUILD_NUMBER ."
        }
      }
    }
    stage('Push Image To Docker Hub') {
      steps{
        script {
          sh "echo $USER"
          sh "docker login -u deepakramanan -p 9994522727"
          sh "docker push deepakramanan/cicd-poc-docker-jenkins-ansible:$BUILD_NUMBER"
          }
        }
      }
    }
}

