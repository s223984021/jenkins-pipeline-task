pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the project...'
                    sh 'mvn clean package'  // Replace with appropriate build command for your language
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests...'
                    sh 'mvn test'  // Replace with appropriate test command for your language
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Analyzing code quality...'
                    sh 'sonar-scanner'  // Replace with appropriate code analysis command
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan...'
                    sh 'dependency-check --scan .'  // Replace with appropriate security scan command
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to staging environment...'
                    sh 'ansible-playbook deploy_staging.yml'  // Replace with appropriate deploy command
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging...'
                    sh 'postman-collection-runner'  // Replace with appropriate integration test command
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production...'
                    sh 'ansible-playbook deploy_production.yml'  // Replace with appropriate deploy command
                }
            }
        }
    }

    post {
        always {
            script {
                echo 'Pipeline completed.'
            }
        }
        success {
            mail to: 's223984021@deakin.edu.au',
                 subject: "SUCCESS: Jenkins Pipeline",
                 body: "Pipeline was successful. Logs are attached.",
                 attachLog: true
        }
        failure {
            mail to: 's223984021@deakin.edu.au',
                 subject: "FAILURE: Jenkins Pipeline",
                 body: "Pipeline failed. Logs are attached.",
                 attachLog: true
        }
    }
}

