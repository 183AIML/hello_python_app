pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
               git credentialsId: 'PAThelloworldtoken', url: 'https://github.com/183AIML/hello_python_app.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'python3 -m venv venv'
                bat '. venv/bin/activate && pip install -r requirement.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat '. venv/bin/activate && pytest test_hello.py'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application...'
                bat '. venv/bin/activate && python hello_world.py'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
