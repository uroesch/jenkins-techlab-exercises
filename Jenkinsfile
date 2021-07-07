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
        withEnv(["JAVA_HOME=${tool 'jdk11'}", "PATH+MAVEN=${tool 'maven36'}/bin:${env.JAVA_HOME}/bin"]) {
          checkout scm
          sh 'mvn -B -V -U -e clean verify -Dsurefire.useFile=false -DargLine="-Djdk.net.URLClassPath.disableClassPathURLCheck=true"'
          archiveArtifacts 'target/*.?ar'
          junit 'target/**/*.xml'
        }
      }
    }
  }
}
