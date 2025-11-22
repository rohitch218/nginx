pipeline {
    agent any

    stages {

        stage('Install Nginx') {
            steps {
                sh '''
                     apt-get update -y
                     apt-get install nginx -y || true
                     systemctl enable nginx
                     systemctl start nginx
                '''
            }
        }

        stage('Deploy index.html') {
            steps {
                sh '''
                     rm -f /var/www/html/index.html
                     cp index.html /var/www/html/index.html
                     chown www-data:www-data /var/www/html/index.html
                '''
            }
        }

        stage('Restart Nginx') {
            steps {
                sh 'systemctl restart nginx'
            }
        }
    }
}
