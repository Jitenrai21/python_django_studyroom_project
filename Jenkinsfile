pipeline {
  agent any
  stages {
    stage('Build in Docker') {
      steps {
        script {
          def winWorkspace = "${env.WORKSPACE}"
          def linuxWorkspace = winWorkspace.replaceAll('C:', '').replaceAll('\\\\', '/').replaceAll(' ', '\\ ')
          linuxWorkspace = "/c" + linuxWorkspace

          echo "Linux workspace: ${linuxWorkspace}"

          bat """
          docker run --rm -v ${linuxWorkspace}:/workspace -w /workspace python:3.13.5-alpine3.22 python --version
          """
        }
      }
    }
  }
}
