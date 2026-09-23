pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Restoring a clean app.py without unused imports...'
                writeFile file: 'app.py', text: '''def greet(name):
    print(f"Hello, {name}")
'''
            }
        }
        
        stage('Show Build Info') {
            steps {
                echo "BUILD_NUMBER: ${env.BUILD_NUMBER}"
                echo "JOB_NAME: ${env.JOB_NAME}"
                echo "WORKSPACE: ${env.WORKSPACE}"
            }
        }
        
        stage('Run Linter') {
            steps {
                echo 'Running flake8 linter...'
                bat 'pip install flake8'
                bat 'flake8 app.py'
            }
        }
    }
}
