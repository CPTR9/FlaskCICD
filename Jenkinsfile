pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                // Clone the Git repository
                git branch: 'main', url: 'https://github.com/user/repo.git'
            }
        }

        stage('Install dependencies') {
            steps {
                // Install dependencies using pip in a virtual environment
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                // Run tests using pytest
                sh './venv/bin/pytest'
            }
        }

        stage('Run Flask App') {
            steps {
                // Run the Flask app (in development mode)
                sh './venv/bin/flask run'
            }
        }
    }

    post {
        always {
            // Cleanup actions, or other post-build steps
            echo 'Pipeline completed.'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed. Check logs for details.'
        }
    }
}
