pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'YOUR_REPO_URL_HERE'
            }
        }

        stage('Install Node.js') {
            steps {
                sh '''
                # Install Node if not installed
                if ! command -v node &> /dev/null
                then
                  curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
                  sudo apt-get install -y nodejs
                fi

                node -v
                npm -v
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
    }

    post {
        success {
            echo "Build completed successfully!"
        }
        failure {
            echo "Build failed!"
        }
    }
}
