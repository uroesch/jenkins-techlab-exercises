pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
    timeout(time: 10, unit: 'MINUTES')
    timestamps()  // Timestamper Plugin
    disableConcurrentBuilds()
  }
  stages {
    stage('Greeting') {
      steps {
        echo 'Hello, World!'
      }
    }
  }
}
