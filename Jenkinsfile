pipeline {
  agent {
    node {
      label 'master'
    }
    
  }
  stages {
    stage('Test-docker - Checkout') {
      steps {
        git(url: 'https://github.com/rkum79/npm-test-demo', branch: 'master', changelog: true, credentialsId: 'b7fa7a585f975c4caa1dde7ae4570a5b44b452ab', poll: true)
      }
    }
    stage('Test-docker - Build') {
      steps {
        build 'docker-build-job'
        dockerNode(image: 'npm-test-demo-image:v${BUILD_NUMBER}', socket: true) {
          echo 'Build created'
        }
        
      }
    }
    stage('status') {
      steps {
        sh 'docker images'
      }
    }
  }
}
