pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn clean package'  // Replace with the appropriate command for your project
            }
        }
        // Add additional stages here
    }

    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            mail to: 'your-email@example.com',
                 subject: "SUCCESS: Jenkins Pipeline",
                 body: "Pipeline was successful. Logs are attached.",
                 attachLog: true
        }
        failure {
            mail to: 'your-email@example.com',
                 subject: "FAILURE: Jenkins Pipeline",
                 body: "Pipeline failed. Logs are attached.",
                 attachLog: true
        }
    }
}

