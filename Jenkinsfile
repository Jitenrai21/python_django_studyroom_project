pipeline {
    agent any
    environment {
        VENV = 'venv'
    }
    stages {
        stage('Check Out') {
            steps {
                git branch: 'main', url: 'https://github.com/Jitenrai21/python_django_studyroom_project.git'
            }
        }

        stage('Set up VENV') {
            steps {
                bat 'python -m venv %VENV%'
                bat '%VENV%\\Scripts\\python -m pip install --upgrade pip'
                bat '%VENV%\\Scripts\\pip install -r requirements.txt'
            }
        }

        // stage('Run Django Commands') {
        //     steps {
        //         bat '''
        //             %VENV%\\Scripts\\python tournaments\\manage.py migrate
        //             %VENV%\\Scripts\\python tournaments\\manage.py collectstatic --noinput
        //             %VENV%\\Scripts\\python tournaments\\manage.py test
        //         '''
        //     }
        // }

        stage('Start Dev Server') {
            steps {
                bat '''
                    cd StudyRoomProject
                    start /B ..\\venv\\Scripts\\python manage.py runserver 0.0.0.0:8000
                '''
            }
        }

        stage('Approval') {
            steps {
                script {
                    input message: "Approve to deploy production server on port 8001?", ok: "Deploy"
                }
            }
        }

        stage('Run Production Server') {
            steps {
                bat '''
                    cd StudyRoomProject
                    start /B ..\\%VENV%\\Scripts\\python manage.py runserver 0.0.0.0:8001
                '''
            }
        }
    }
}
