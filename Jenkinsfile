properties([
  buildDiscarder(logRotator(numToKeepStr: '5'))
])

timestamps() {
  timeout(time: 10, unit: 'MINUTES') {
    node {
      stage('Greeting') {
        withEnv(['GREETINGS_TO=Jenkins Techlab']) {
          echo "Hello, ${env.GREETINGS_TO} !"
          // also available as env variable to a process:
          sh 'echo "Hello, $GREETINGS_TO !"'
        }
      }
    }
  }
}

