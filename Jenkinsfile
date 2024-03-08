pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository
                git branch: 'master', url: 'https://github.com/shehabosama/jenkins_test_ci_cd.git'
            }
        }

        stage('Build') {
            steps {
                // Build the Android project
                bat 'gradlew.bat assembleDebug'
            }
        }

        stage('Run Tests') {
            steps {
                // Run unit tests for the Android project
                bat 'gradlew.bat test'
            }
        }

        stage('Archive APK') {
            steps {
                // Archive the generated APK file
                archiveArtifacts artifacts: 'app/build/outputs/apk/debug/*.apk'
            }
        }
    }

    post {
        always {
            // Clean up workspace after the build
            cleanWs()
        }
    }
}