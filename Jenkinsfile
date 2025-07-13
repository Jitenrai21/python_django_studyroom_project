pipeline {
  agent any
  stages {
    stage('Run in Python container') {
      steps {
        script {
          // Compose the Linux-style path for the workspace
          def winWorkspace = "${env.WORKSPACE}"
          def linuxWorkspace = winWorkspace.replaceAll('C:', '').replaceAll('\\\\', '/').replaceAll(' ', '\\ ')
          linuxWorkspace = "/c" + linuxWorkspace

          echo "Linux-style workspace path: ${linuxWorkspace}"

          def myImage = docker.image('python:3.13.5-alpine3.22')

          myImage.inside("-v ${linuxWorkspace}:/workspace -w /workspace") {
            sh 'python --version'
            sh 'ls -la'
          }
        }
      }
    }
  }
}
