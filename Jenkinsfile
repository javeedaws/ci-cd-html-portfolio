pipeline {
    agent any

    stages {
        stage('Deploy to Apache') {
            steps {
                sh '''
                echo "Deploying HTML website to /var/www/html/dist ..."

                # NEVER delete the dist directory itself
                sudo rm -rf /var/www/html/dist/*

                # Copy build files
                sudo cp -r dist/* /var/www/html/dist/

                # Permissions
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
