pipeline {
    agent any
     tools {
            // Specify the Git tool installation
            git 'GIT'
        }

    stages {
        stage('Build App') {
            steps {
                // Clean and assemble APKs
                sh './gradlew clean assembleDebug assembleDebug'
            }
        }
//         stage('Archive Files') {
//             steps {
//                 // Archive the APKs so that they can be downloaded from Jenkins
//                 echo 'Archiving APKs...'
//                 archiveArtifacts '**/*.apk'
//             }
//         }
        stage('Finished') {
            steps {
                echo 'Finished'
            }
        }
    }
}
