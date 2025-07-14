/* Requires the Docker Pipeline plugin */
pipeline {
    agent any 
    stages {
        stage('build') {
            steps {
                bat 'echo "Hello World"'
                bat '''
                    echo "Multiline shell steps works too"
                '''
            }
        }
    }
}
