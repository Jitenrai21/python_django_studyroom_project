/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'python:3.13.5-alpine3.22' } }
    stages {
        stage('build') {
            steps {
                bat 'echo "Hello World"'
                bat '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
    }
}
