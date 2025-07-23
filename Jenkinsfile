pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/Jitenrai21/python_django_studyroom_project.git'
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

        stage('Deploy to Staging') {
            steps {
                bat '''
                taskkill /F /IM python.exe > nul 2>&1
                cd webapp\\StudyRoom
                pip install -r ..\\requirements.txt
                start /B python manage.py runserver 0.0.0.0:8000
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
                start /B python manage.py runserver 0.0.0.0:8001
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
