pipeline {
  agent {
    kubernetes {
      label 'jenkin-slave'  
      yamlFile 'jenkins-worker-pod.yaml'
      defaultContainer 'ubuntu'
    }
  }
  stages {
    stage('Build') {
      steps { 
        sh "echo this is Build stage"   
      }
    }
    stage('Docker') {
      steps {
        container('docker') {  
          sh "docker version"        
        }
      }
    }
    stage('Deploy') {
      steps {
        container('ubuntu') {  
          sh "echo this is Deploy stage"        
        }
      }
    }
  }
}
