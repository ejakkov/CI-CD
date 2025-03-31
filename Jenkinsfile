pipeline {
    agent any

    stages {
        stage('install-pip-deps') {
            steps {
                echo 'Installing Python dependencies using pip...'
                // bat 'pip install -r requirements.txt'
                sh "ls"
            }
        }

        stage('deploy-to-dev') {
            steps {
                echo 'Deploying to development environment...'
                // bat 'call deploy-dev.bat'
            }
        }

        stage('tests-on-dev') {
            steps {
                echo 'Running tests on development environment...'
                // bat 'call test-dev.bat'
            }
        }

        stage('deploy-to-staging') {
            steps {
                echo 'Deploying to staging environment...'
                // bat 'call deploy-staging.bat'
            }
        }

        stage('tests-on-staging') {
            steps {
                echo 'Running tests on staging environment...'
                // bat 'call test-staging.bat'
            }
        }

        stage('deploy-to-preprod') {
            steps {
                echo 'Deploying to pre-production environment...'
                // bat 'call deploy-preprod.bat'
            }
        }

        stage('tests-on-preprod') {
            steps {
                echo 'Running tests on pre-production environment...'
                // bat 'call test-preprod.bat'
            }
        }

        stage('deploy-to-prod') {
            steps {
                echo 'Deploying to production environment...'
                // bat 'call deploy-prod.bat'
            }
        }

        stage('tests-on-prod') {
            steps {
                echo 'Running tests on production environment...'
                // bat 'call test-prod.bat'
            }
        }
    }
}
