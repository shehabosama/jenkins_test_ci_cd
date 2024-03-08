pipeline {
    agent any
 tools {
        // Specify the JDK tool installation by name and version
        jdk 'JAVA_HOME'
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository
                git branch: 'master', url: 'https://github.com/shehabosama/jenkins_test_ci_cd.git'
            }
        }

        stage('Build APK') {
            steps {
                // Use Gradle to build the APK
                script {
                    // For Unix-based systems (Linux, macOS)
                    //sh './gradlew clean assembleDebug'

                    // For Windows
                     bat 'gradlew.bat clean assembleDebug'
                }
            }
        }
    }

    post {
        success {
            // Archive the APK if the build succeeds
            archiveArtifacts artifacts: '**/*.apk'
        }
    }
}
