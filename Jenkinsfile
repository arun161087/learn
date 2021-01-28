pipeline {
  agent {
    kubernetes {
      label 'jenkins-worker'
      idleMinutes 10
      yamlFile 'jenkins-worker-pod.yaml'
      defaultContainer 'ubuntu'
    }
  }
  stages {
    stage('Build') {
      steps {  // If we do not define any container then default will be used
        sh "Hi This is build stage"   
      }
    }
    stage('Build Docker Image') {
      steps {
        container('docker') {  
          sh "docker version" 
        }
      }
    }
  }
}
