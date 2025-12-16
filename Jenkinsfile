pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Repository cloned by Jenkins automatically'
            }
        }

        stage('Install Backend Dependencies') {
            steps {
                dir('backend') {
                    sh 'pip3 install -r requirements.txt || true'
                }
            }
        }

        stage('Restart Flask Backend') {
            steps {
                sh '''
                pm2 restart flask-backend || pm2 start "python3 backend/app.py" --name flask-backend
                '''
            }
        }
    }
}
