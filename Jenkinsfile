pipeline {
    agent any

    triggers {
        cron('H/2 * * * *')        // Build every 2 minutes
        pollSCM('H/1 * * * *')     // Check repo every 1 minute
    }

    stages {

        stage('Clone Repository') {
            steps {
                echo "Cloning repository..."
                git 'https://github.com/amankr59/jenkins-pipeline.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building project..."
                sh 'echo Build Successful > build.txt'
            }
        }

        stage('Echo Build Status') {
            steps {
                echo "Build completed successfully!"
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'build.txt', fingerprint: true
            }
        }
    }
}
