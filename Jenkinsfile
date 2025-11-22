pipeline {
    agent any

    stages {

        stage('Clone from GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/rohitch218/nginx.git'
            }
        }

        stage('Install Nginx') {
            steps {
                sh 'sudo apt-get update -y'
                sh 'sudo apt-get install nginx -y'
                
            }
        }

        stage('Deploy index.html to Nginx') {
            steps {
                sh 'sudo cp index.html /var/www/html/index.html'
            }
        }

        stage('Restart Nginx') {
            steps {
                sh 'sudo systemctl restart nginx'
            }
        }
    }
}
