pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                deleteDir()
                git branch: 'main',
                    url: 'https://github.com/javeedaws/ci-cd-html-portfolio.git'
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                echo "Deploying website..."

                rm -rf /var/www/html/dist/*
                cp -r dist/* /var/www/html/dist/
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful'
        }
        failure {
            echo '❌ Deployment failed'
        }
    }
}
