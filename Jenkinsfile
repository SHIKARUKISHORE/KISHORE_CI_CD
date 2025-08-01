pipeline {
    agent any 

    tools {
        nodejs 'Nodejs_22'
    }
     environment {
        FRONTEND_DIR = 'CLIENT_KISHORE'
        BACKEND_DIR = 'SERVER_RAM'
        BACKEND_PUBLISH_DIR = 'SERVER_RAM/publish_output'
        FRONTEND_BUILD_DIR = 'CLIENT_KISHORE/build'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/SHIKARUKISHORE/KISHORE_CI_CD.git', branch: 'main'
            }
        }

        stage('Install Frontend') {
            steps {
                dir('CLIENT_KISHORE') {
                    bat 'npm install'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('CLIENT_KISHORE') {
                    bat 'npm run build'
                }
            }
        }

        stage('Restore Backend Dependencies') {
            steps {
                dir('SERVER_RAM') {
                    bat 'dotnet restore'
                }
            }
        }

        stage('Build Backend') {
            steps {
                dir('SERVER_RAM') {
                    bat 'dotnet build --configuration Release'
                }
            }
        }

        stage('Publish Backend') {
            steps {
                dir('SERVER_RAM') {
                    bat 'dotnet publish --configuration Release -o publish_output'
                }
            }
        }
    }
}