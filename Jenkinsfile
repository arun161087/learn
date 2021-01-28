pipeline {
  agent {
    kubernetes {
      idleMinutes 10
      yamlFile 'jenkins-worker-pod.yaml'
      defaultContainer 'ubuntu'
    }
  }
  stages {
    stage('BUILD') {
      steps {  // If we do not define any container then default will be used
        sh "Hi This is build stage"   
      }
    }
    stage('DOCKER') {
      steps {
        container('docker') {  
          sh "docker version" 
        }
      }
    }
  }
}
