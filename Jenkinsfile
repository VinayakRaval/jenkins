pipeline {
    agent any

    tools {
        maven 'Maven-3'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/VinayakRaval/jenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Upload to S3') {
            steps {
                s3Upload(
                    bucket: 'artifactbucketfornetflixapp',
                    region: 'ap-south-1',
                    file: 'target/NETFLIX.war'
                )
            }
        }

        stage('Deploy') {
            steps {
                echo "Application Deployed Successfully 🚀"
            }
        }
    }
}