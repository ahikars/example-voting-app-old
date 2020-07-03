pipeline {
  agent {
    node {
      label 'ubuntu-1604-aufs-stable'
    }
  }
  stages {
    stage('Build result') {
      steps {
        sh 'docker build -t ahikars/result ./result'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'docker build -t ahikars/vote ./vote'
      }
    }
    stage('Build worker') {
      steps {
        sh 'docker build -t ahikars/worker ./worker'
      }
    }
    stage('Push result image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerbuildbot-index.docker.io', url:'') {
          sh 'docker push ahikars/result'
        }
      }
    }
    stage('Push vote image') {
            steps {
        withDockerRegistry(credentialsId: 'dockerbuildbot-index.docker.io', url:'') {
          sh 'docker push ahikars/vote'
        }
      }
    }
    stage('Push worker image') {
     
      steps {
        withDockerRegistry(credentialsId: 'dockerbuildbot-index.docker.io', url:'') {
          sh 'docker push ahikars/worker'
        }
      }
    }
  }
}