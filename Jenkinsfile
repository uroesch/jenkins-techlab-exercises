pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
    timeout(time: 10, unit: 'MINUTES')
    timestamps()  // Timestamper Plugin
    disableConcurrentBuilds()
  }
  triggers {
      pollSCM('H/5 * * * *')
  }
  stages {
    stage('Build') {
      steps {
        script {
          def company = 'puzzle'
          echo 'join the ${company}'
          echo "join the ${company}"
          echo '''join the ${company}'''
          echo """join the ${company}"""

          echo "tabulation>\t<"
          echo "backspace>\b<"
          echo "newline>\n<"
          echo "carriage return>\r<"
          echo "form feed>\f<"
          echo "backslash>\\<"
          echo "single quote>\'<"
          echo "double quote>\"<"
        }
      }
    }
  }
}
