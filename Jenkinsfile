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
    stage('Build') {
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
      stage('Notification') {
        steps {
          emailext(subject: '$BUILD_NUMBER $BUILD_STATUS', body: '$BUILD_STATUS', attachLog: true, attachmentsPattern: 'tar.gz', compressLog: true, from: 'simon@jenkins.com', replyTo: 'rkumar113@sapient.com', to: 'rkumar113@sapient.com')
        }
      }
    }
  }