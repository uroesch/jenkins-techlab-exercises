pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
    timeout(time: 10, unit: 'MINUTES')
    timestamps()  // Timestamper Plugin
    disableConcurrentBuilds()
  }
  parameters {
    string(name: 'Greetings_to', defaultValue: 'Jenkins Techlab', description: 'Who to greet?')
  }
  stages {
    stage('Greeting') {
      steps {
        echo "Hello, ${params.Greetings_to}!"
      }
    }
  }
}
