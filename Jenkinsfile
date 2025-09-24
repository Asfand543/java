pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Asfand543/react.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "📦 Installing dependencies..."
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo "⚡ Building the React app..."
                bat 'npm run build'
            }
        }

        stage('Archive Build') {
            steps {
                echo "📂 Archiving production build..."
                archiveArtifacts artifacts: 'dist/**', followSymlinks: false
            }
        }
    }

    post {
        success {
            echo "✅ Build completed successfully!"
        }
        failure {
            echo "❌ Build failed. Check logs!"
        }
    }
}
