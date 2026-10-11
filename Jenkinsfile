// =======================================================
// Jenkinsfile — Pipeline for MyWebApp
// =======================================================
// This pipeline automates:
//   1. Fetching code from GitHub
//   2. Deploying to Apache Tomcat
// =======================================================

pipeline {
    agent any

    environment {
        TOMCAT_WEBAPPS = 'C:\\apache-tomcat\\webapps\\MyWebApp'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Fetching source code from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'No build step required for static HTML.'
                echo 'In a real project, this would compile code, run tests, etc.'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                echo 'Deploying to Apache Tomcat...'
                bat "if not exist \"${TOMCAT_WEBAPPS}\" mkdir \"${TOMCAT_WEBAPPS}\""
                bat "xcopy /s /y \"${WORKSPACE}\\index.html\" \"${TOMCAT_WEBAPPS}\\\""
                echo 'Deployment complete!'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
            echo 'Open http://localhost:8081/MyWebApp/ to view the app.'
        }
        failure {
            echo '❌ Pipeline failed. Check the console output for errors.'
        }
    }
}
