pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/Jitenrai21/python_django_studyroom_project.git'
        VENV = 'venv'
    }

    stages {
        stage('Clone Repo') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'GITHUB_PAT', usernameVariable: 'GIT_USER', passwordVariable: 'GIT_PAT')]) {
                    bat '''
                    if exist webapp (rmdir /s /q webapp)
                    git clone https://%GIT_USER%:%GIT_PAT%@github.com/Jitenrai21/python_django_studyroom_project.git webapp
                    '''
                }
            }
        }
        stage('Set up VENV') {
            steps {
                bat 'python -m venv %VENV%'
                bat '%VENV%\\Scripts\\python -m pip install --upgrade pip'
                bat '%VENV%\\Scripts\\pip install -r requirements.txt'
            }
        }
        stage('Deploy to Staging') {
            steps {
                bat '''
                taskkill /F /IM python.exe > nul 2>&1
                cd webapp\\StudyRoom
                start /B ..\\venv\\Scripts\\python manage.py runserver 0.0.0.0:8000
                '''
            }
        }

        stage('Manual Approval') {
            steps {
                input message: 'Deploy to Production?'
            }
        }

        stage('Deploy to Production') {
            steps {
                bat '''
                taskkill /F /IM python.exe > nul 2>&1
                cd webapp\\StudyRoom
                start /B ..\\venv\\Scripts\\python manage.py runserver 0.0.0.0:8000
                '''
            }
        }

        
        stage('testin to VM2') {
            steps {
                input message: 'Is working in VM2?'
            }
        }
    }
}
