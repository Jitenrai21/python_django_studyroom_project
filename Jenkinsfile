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
    post{
        always{
            echo 'This will always run'
        }
        success{
            echo 'This will run if successful!'
        }
        failure{
            echo 'This will run if failure!'
        }
        unstable{
            echo 'This will run only if the wun was marked as unstable!'
        }
    }
}
