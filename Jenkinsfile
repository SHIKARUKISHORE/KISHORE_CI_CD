pipeline {
  agent any

  tools {
    nodejs 'Nodejs_18'
    
  }
environment {
    path = "C:\\Users\\Kishore Shikaru"


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
          sh 'npm install'
        }
      }
    }

    stage('Build Frontend') {
      steps {
        dir('frontend') {
          sh 'npm run build'
        }
      }
    }

    stage('Build Backend') {
      steps {
        dir('backend') {
          sh 'dotnet restore'
          sh 'dotnet build --configuration Release'
        }
      }
    }

    stage('Publish Backend') {
      steps {
        dir('backend') {
          sh 'dotnet publish -c Release -o out'
        }
      }
    }

    stage('Deploy (Optional)') {
      steps {
        echo 'Deploy backend and frontend from here (IIS, Azure, Docker, etc).'
      }
    }

    stage('Complete') {
      steps {
        echo '✅ Build pipeline complete!'
      }
    }
  }
}
