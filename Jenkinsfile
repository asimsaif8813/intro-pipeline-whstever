pipeline {
  agent {
    label 'jdk9'
  }
  stages {
    stage('Say Hello') {
      steps {
        echo 'Say Hello '
        sh 'java -version'
      }
    }
  }
}