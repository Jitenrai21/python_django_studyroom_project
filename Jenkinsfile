// pipeline {
//     agent any

//     environment {
//         GIT_REPO = 'github.com/Jitenrai21/python_django_studyroom_project.git'
//         GIT_USER = 'Jitenrai21'
//     }

//     stages {
//         stage('Deploy to Staging') {
//             steps {
//                 withCredentials([string(credentialsId: 'GITHUB_PAT', variable: 'GIT_PAT')]) {
//                     sh """
//                         ssh user@vm1-ip << EOF
//                             pkill -f "python3 manage.py runserver" || true
//                             rm -rf webapp || true
//                             git clone https://${GIT_USER}:${GIT_PAT}@github.com/Jitenrai21/python_django_studyroom_project.git webapp
//                             cd webapp
//                             pip3 install -r requirements.txt
//                             nohup python3 manage.py runserver --port=8000 > app.log 2>&1 &
//                         EOF
//                     """
//                 }
//             }
//         }

//         stage('Manual Approval') {
//             steps {
//                 input message: 'Deploy to Production?'
//             }
//         }

//         stage('Deploy to Production') {
//             steps {
//                 withCredentials([string(credentialsId: 'GITHUB_PAT', variable: 'GIT_PAT')]) {
//                     sh """
//                         ssh user@vm2-ip << EOF
//                             pkill -f "python3 manage.py runserver" || true
//                             rm -rf webapp || true
//                             git clone https://${GIT_USER}:${GIT_PAT}@github.com/Jitenrai21/python_django_studyroom_project.git webapp
//                             cd webapp
//                             pip3 install -r requirements.txt
//                             nohup python3 manage.py runserver --port=8001 > app.log 2>&1 &
//                         EOF
//                     """
//                 }
//             }
//         }
//     }
// }


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
