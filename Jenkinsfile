pipeline {
    agent any

    tools {
        nodejs 'NodeJS'   // Name from Global Tool Configuration
    }

    environment {
        AWS_DEFAULT_REGION = "us-east-1"
        S3_BUCKET = "my-react-app-bucket-03"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Dineshpardhu12/pro.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy to S3') {
            steps {
                sh 'aws s3 sync dist/ s3://$S3_BUCKET/ --delete'
            }
        }
    }
}
