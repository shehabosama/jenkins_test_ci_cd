pipeline {
    agent any
    environment {
        // Fastlane Environment Variables
        PATH = "$HOME/.fastlane/bin:" +
                "$HOME/.rvm/gems/ruby-2.5.3/bin:" +
                "$HOME/.rvm/gems/ruby-2.5.3@global/bin:" +
                "$HOME/.rvm/rubies/ruby-2.5.3/bin:" +
                "/usr/local/bin:" +
                "$PATH"
        LC_ALL = "en_US.UTF-8"
        LANG = "en_US.UTF-8"

        VERSION_NAME = ""
        VERSION_SUFFIX = ""
        APP_VERSION_NAME = ""
        VERSION_CODE = ""
        DROPBOX_FOLDER = ""
        PROGUARD_ENABLED = ""
        JIRA_PROJECT_KEY = ""
        PROJECT_NAME = env.JOB_NAME.tokenize("/").first().replaceAll(" Android", "")
    }
    stages {
        stage('Build App') {
            steps {
                // Clean and assemble APKs
                sh './gradlew clean assembleDebug assembleDebug'
            }
        }
        stage('Archive Files') {
            steps {
                // Archive the APKs so that they can be downloaded from Jenkins
                echo 'Archiving APKs...'
                archiveArtifacts '**/*.apk'
            }
        }
        stage('Finished') {
            steps {
                echo 'Finished'
            }
        }
    }
}
