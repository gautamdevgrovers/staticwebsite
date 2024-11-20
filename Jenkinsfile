pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Cloning the repository
                git 'https://github.com/gautamdevgrovers/staticwebsite.git'
            }
        }

        stage('Build') {
            steps {
                // Placeholder for build tasks
                echo 'No build step required for static site.'
            }
        }

        stage('Deploy') {
            steps {
                // Copy files to the deployment directory
                sh '''
                mkdir -p /var/www/html
                cp -r * /var/www/html
                '''
            }
        }
    }
}
