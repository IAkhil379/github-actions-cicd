pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m pip install --upgrade pip
                    pip3 install -r requirements.txt
                '''
            }
        }
        stage('Run Tests') {
            steps { sh 'pytest test_app.py' }
        }
        stage('Deploy') {
            when { branch 'main' }
            steps {
                sh '''
                    echo "Pushing code to production server..."
                    echo "Deployment successful!"
                '''
            }
        }
    }
}
