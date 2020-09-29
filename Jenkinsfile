pipeline {

    agent any
    
    environment {
    }
    
    stages {

        stage('Build') {
            steps {
                sh 'docker-compose up -d --build site'
            }
        }

        stage('Test') {
            steps {
                sh 'docker-compose run --rm composer update'
            }
        }

        stage('Push') {
            steps {
                sh 'docker-compose run --rm npm run dev'
            }
        }

        stage('Deploy') {
            steps {
                sh "docker-compose run --rm artisan migrate"
            }
        }
    }
}
