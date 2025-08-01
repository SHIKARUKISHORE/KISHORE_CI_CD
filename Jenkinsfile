pipeline {
    agent any

    tools {
        nodejs 'NodeJS 18'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/SHIKARUKISHORE/KISHORE_CI_CD.git', branch: 'main'
            }
        }

        stage('Install Frontend') {
            steps {
                dir('frontend') {
                    bat 'npm install'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    bat 'npm run build'
                }
            }
        }

        stage('Build Backend') {
            steps {
                dir('backend') {
                    bat 'dotnet build'
                }
            }
        }

        stage('Publish Backend') {
            steps {
                dir('backend') {
                    bat 'dotnet publish -c Release -o published'
                }
            }
        }

        stage('Deploy (Optional)') {
            steps {
                echo 'Deploy step would go here...'
            }
        }

        stage('Complete') {
            steps {
                echo 'CI/CD pipeline completed successfully!'
            }
        }
    }
}


