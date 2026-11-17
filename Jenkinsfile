pipeline {
    agent any

    triggers {
        githubPush()
    }

    options {
        skipDefaultCheckout(true)
        timestamps()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    if (!fileExists('manage.html')) {
                        error('Build failed: manage.html was not found.')
                    }
                }
                archiveArtifacts artifacts: 'manage.html', fingerprint: true
            }
        }
    }
}
