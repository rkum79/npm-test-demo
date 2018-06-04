pipeline {
    agent none 
    stages {
        stage('Docker_build - Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '587adf48-114e-49cc-8e19-52bce59625a3', url: 'https://github.com/rkum79/npm-test-demo.git']]])
            }
        }
        stage('Docker_build - Build') {
            steps {
                dir('${WORKSPACE}') {
                    docker.build("npm-test-demo-image:v${BUILD_NUMBER}")
            }
        }
    }
}
