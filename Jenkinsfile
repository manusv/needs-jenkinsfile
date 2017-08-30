pipeline {
  agent {
    docker {
      image 'rowanto/docker-java8-mvn-nodejs-npm'
    }
    
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
  }
}