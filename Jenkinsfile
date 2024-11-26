pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Cloning the repository
                git branch: 'main',
                    url: 'https://github.com/gautamdevgrovers/staticwebsite.git'
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
                mkdir /tmp/dep
                cp -r * /tmp/dep
                '''
            }
        }
    }

    post {
        success {
            // Send email on successful build
            emailext(
                subject: "Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
                <p>Hi Team,</p>
                <p>The Jenkins pipeline for the project <b>${env.JOB_NAME}</b> has completed successfully.</p>
                <p><b>Build Number:</b> ${env.BUILD_NUMBER}</p>
                <p><b>Build URL:</b> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                """,
                to: 'pankaj.pundir@unthinkable.co'
            )
        }
        failure {
            // Send email on failed build
            emailext(
                subject: "Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
                <p>Hi Team,</p>
                <p>The Jenkins pipeline for the project <b>${env.JOB_NAME}</b> has failed.</p>
                <p><b>Build Number:</b> ${env.BUILD_NUMBER}</p>
                <p><b>Build URL:</b> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                """,
                to: 'pankaj.pundir@unthinkable.co'
            )
        }
    }
}
}
