pipeline {
    agent any
    environment {
        PATH = "C:\\Users\\ervin\\AppData\\Local\\Programs\\Python\\Python39;$PATH"
    }
    stages {
        stage('install-pip-deps') {
            steps {
                echo 'Cleaning up any existing python-greetings folder...'
                bat 'if exist python-greetings rmdir /s /q python-greetings'
                echo 'Cloning repository...'
                bat 'git clone https://github.com/mtararujs/python-greetings.git'
                echo 'PYTHONPATHL:' 

                bat "echo %PYTHONPATH%"
                echo 'Listing contents of cloned repository...'
                bat 'dir python-greetings'

                echo 'Check python...'
                bat 'python --version' 

                bat 'python -m pip install -r python-greetings\\requirements.txt'
            }
        }

        stage('deploy-to-dev') {
            steps {
                echo 'Deploying to development environment...'
                bat 'if exist python-greetings rmdir /s /q python-greetings'
                bat 'git clone https://github.com/mtararujs/python-greetings.git'
        
                echo 'Stopping any existing PM2 app for dev...'
                bat 'pm2 delete greetings-app-dev & EXIT /B 0'
        
                echo 'Starting PM2 app for dev on port 7001...'
                bat 'pm2 start app.py --name greetings-app-dev -- --port 7001'
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
