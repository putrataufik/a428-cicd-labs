pipeline {
    agent {
        docker {
            image 'node:16-buster-slim'      // Pakai image Docker Node.js untuk build
            args '-p 3000:3000'              // Publish port 3000 dari container
        }
    }
    stages {
        stage('Build') {                     // Tahap Build
            steps {
                sh 'npm install'             // Install semua dependencies React App
            }
        }
    }
}
