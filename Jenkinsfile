pipeline {
    agent any
    environment {
        PATH = "C:\\Users\\ervin\\AppData\\Local\\Programs\\Python\\Python39;$PATH"
    }
    stages {
        stage('install-pip-deps') {
            steps {
                script {
                    installDependencies()
                }
            }
        }

        stage('deploy-to-dev') {
            steps {
                script {
                    deploy('dev', 7001)
                }
            }
        }

        stage('tests-on-dev') {
            steps {
                script {
                    test('dev')
                }
            }
        }

        stage('deploy-to-staging') {
            steps {
                script {
                    deploy('staging', 7002)
                }
            }
        }

        stage('tests-on-staging') {
            steps {
                script {
                    test('staging')
                }
            }
        }

        stage('deploy-to-preprod') {
            steps {
                script {
                    deploy('preprod', 7003)
                }
            }
        }

        stage('tests-on-preprod') {
            steps {
                script {
                    test('preprod')
                }
            }
        }

        stage('deploy-to-prod') {
            steps {
                script {
                    deploy('prod', 7004)
                }
            }
        }

        stage('tests-on-prod') {
            steps {
                script {
                    test('prod')
                }
            }
        }
    }
}

def cloneIfNotExist(repoName, repoUrl) {
    bat "IF NOT EXIST ${repoName} git clone ${repoUrl}"
}

def installDependencies() {
    echo 'Checking if python-greetings repo is already cloned...'
    cloneIfNotExist('python-greetings', 'https://github.com/mtararujs/python-greetings.git')

    echo 'PYTHONPATH:'
    bat "echo %PYTHONPATH%"
    echo 'Listing contents of cloned repository...'
    bat 'dir python-greetings'
    echo 'Check python...'
    bat 'python --version' 
    bat 'python -m pip install -r python-greetings\\requirements.txt'
}

def deploy(envName, port) {
    echo "Deploying to ${envName} environment..."
    cloneIfNotExist('python-greetings', 'https://github.com/mtararujs/python-greetings.git')
    bat """
        cd python-greetings
        pm2 delete greetings-app-${envName} & EXIT /B 0
        pm2 start app.py --name greetings-app-${envName} -- --port ${port}
    """
}

def test(envName) {
    echo "Running tests on ${envName} environment..."
    cloneIfNotExist('course-js-api-framework', 'https://github.com/mtararujs/course-js-api-framework.git')
    bat """
        cd course-js-api-framework
        npm install
        npm run greetings greetings_${envName}
    """
}
