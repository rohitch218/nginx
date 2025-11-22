pipeline {
    agent any

    stages {

          stage('Clone from GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/rohitch218/nginx.git'
            }
        }

        stage('Install Apache') {
            steps {
                sh '''
                    sudo apt-get update -y
                    sudo apt install apache2
                '''
            }
        }

        stage('Deploy index.html') {
            steps {
                sh '''
                    sudo rm -f /var/www/html/index.html
                    sudo cp index.html /var/www/html/index.html
                    sudo chown www-data:www-data /var/www/html/index.html
                '''
            }
        }

        stage('Restart Apache') {
            steps {
                sh 'sudo systemctl restart nginx'
            }
        }
    }
}
