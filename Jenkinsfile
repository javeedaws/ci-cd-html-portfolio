pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/javeedaws/ci-cd-html-portfolio.git'
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                echo "Deploying HTML website to /var/www/html/dist ..."

                sudo rm -rf /var/www/html/dist/*
                sudo cp -r dist/* /var/www/html/dist/

                sudo chown -R apache:apache /var/www/html/dist
                sudo chmod -R 755 /var/www/html/dist
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
