pipeline {
  agent {
    kubernetes {
      yamlFile 'jenkins-worker-pod.yaml'
      defaultContainer 'maven'
    }
  }
  stages {
    stage('Run maven') {
      steps {
        sh 'set'
        sh "echo OUTSIDE_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}"
        container('maven') {
          sh 'echo MAVEN_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
          sh 'mvn -version'
        }
        container('busybox') {
          sh 'echo BUSYBOX_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
          sh '/bin/busybox'
        }
      }
    }
  }
}
