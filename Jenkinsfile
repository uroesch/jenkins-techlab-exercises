pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
    timeout(time: 10, unit: 'MINUTES')
    timestamps()  // Timestamper Plugin
    disableConcurrentBuilds()
  }
  environment {
    GREETINGS_TO = 'Jenkins Techlab'
  }
  stages {
    stage('Greeting') {
      steps {
        echo "Hello, ${env.GREETINGS_TO}!"
        // also available as env variable to a process:
        sh 'echo "Hello, ${GREETINGS_TO}!"'
      }
    }
  }
}
