pipeline {
  agent any
  stages {
    stage('Prepare') {
      steps {
        sh 'mvnHome = tool \'maven-3.5.3\''
      }
    }
    stage('Build') {
      steps {
        sh '\'${mvnHome}/bin/mvn\' -B -DskipTests clean package'
      }
    }
  }
  environment {
    mvnHome = ''
  }
}