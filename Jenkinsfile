pipeline {
  agent {
    node {
      label 'master'
    } 
  }
  stages {
    stage('Test-docker - Checkout') {
      steps {
        git(url: 'https://github.com/rkum79/npm-test-demo.git', branch: 'master', changelog: true, credentialsId: '587adf48-114e-49cc-8e19-52bce59625a3', poll: true)
      }
    }
    stage('Test-docker - Build') {
      steps {
        docker build("npm-test-demo-image:v${BUILD_NUMBER}") {
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
