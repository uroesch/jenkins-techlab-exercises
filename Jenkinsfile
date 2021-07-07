pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
    timeout(time: 10, unit: 'MINUTES')
    timestamps()  // Timestamper Plugin
    disableConcurrentBuilds()
  }
  tools {
    jdk 'jdk11'
    maven 'maven36'
  }
  stages {
    stage('Greeting') {
      steps {
        sh 'mvn -B -V -U -e clean verify -Dsurefire.useFile=false -DargLine="-Djdk.net.URLClassPath.disableClassPathURLCheck=true"'
        archiveArtifacts 'target/*.?ar'
        junit 'target/**/*.xml'
      }
      post {
        always {
          junit 'target/**/*.xml'
        }
      }
    }
  }
  post {
    success {
      rocketSend (
        avatar: 'https://chat.puzzle.ch/emoji-custom/success.png',
        message: "Build success - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)",
        rawMessage: true
      )
    }
    unstable {
      rocketSend (
        avatar: 'https://chat.puzzle.ch/emoji-custom/unstable.png',
        message: "Build unstable - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)",
        rawMessage: true
      )
    }
    failure {
      rocketSend (
        avatar: 'https://chat.puzzle.ch/emoji-custom/failure.png',
        message: "Build failure - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)",
        rawMessage: true
      )
    }
  }
}
