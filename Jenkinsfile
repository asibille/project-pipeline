pipeline {
    agent any

    triggers {
        githubPush()   // écoute le webhook GitHub
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh './deploy.sh'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline réussie !'
        }
        failure {
            echo '❌ Échec — vérifier les logs.'
        }
    }
}