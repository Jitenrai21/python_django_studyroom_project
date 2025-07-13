/* Requires the Docker Pipeline plugin */
pipeline {
    agent { 
        docker { 
            image 'python:3.13.5-alpine3.22'
            args "-v ${env.WORKSPACE}:/workspace -w /workspace"
        } 
    }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
}
