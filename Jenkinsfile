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

        stage('Deploy index.html only') {
            steps {
                sh '''
                echo "Deploying index.html only..."

                sudo cp dist/index.html /var/www/html/index.html
                sudo chown apache:apache /var/www/html/index.html
                sudo chmod 644 /var/www/html/index.html
                '''
            }
        }
    }

    post {
        success {
            echo '✅ index.html deployed successfully'
        }
        failure {
            echo '❌ Deployment failed'
        }
    }
}
