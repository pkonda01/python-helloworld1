pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  
  stages {
    stage('Checkout') {
      steps {
           git branch: 'main', url: 'https://github.com/pkonda01/python-helloworld1.git'
      }
    }
  }
}
