pipeline { 
 
  agent { 
    node {
      label 'master'
    }
  }
  stage ('Docker_build - Checkout') {
     checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '587adf48-114e-49cc-8e19-52bce59625a3', url: 'https://github.com/rkum79/npm-test-demo.git']]]) 
	}
	
 // stage ('Docker_build - Build') {
//     container = docker.build("-f \${WORKSPACE}/Dockerfile npm-test-demo-image:v\${BUILD_NUMBER}")
//	}
}
