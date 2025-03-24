pipeline {
    agent any

    environment {
        CI_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'develop', url: 'https://github.com/Diansy72/CodeIgniter.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'composer install --no-dev --optimize-autoloader --no-scripts'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'vendor\bin\phpunit'
            }
            post {
                success {
                    junit 'application/tests/results/*.xml'
                }
                failure {
                    echo 'Tests failed!'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to production environment...'
                // Tambahkan perintah deploy sesuai kebutuhan Anda
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
