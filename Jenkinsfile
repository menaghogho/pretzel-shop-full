pipeline {
    aent {
       label 'pretzel_pipeline'
          }


    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-ssh',
                    url: 'git@github.com:menaghogho/pretzel-shop-full.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Start Application') {
            steps {
                sh 'docker compose up -d'
            }
        }

    }

    post {
        success {
            echo 'Build and deployment successful!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
