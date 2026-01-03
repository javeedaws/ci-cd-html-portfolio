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
                echo "Deploying HTML website..."

                sudo rm -rf /var/www/html/*
                sudo cp -r * /var/www/html/

                sudo chown -R apache:apache /var/www/html
                sudo chmod -R 755 /var/www/html

                sudo systemctl restart httpd
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
