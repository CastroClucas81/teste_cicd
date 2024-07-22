pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/CastroClucas81/teste_cicd.git']]])
            }
        }

        stage('Checkout') {
            steps {
                echo "${env.PATH}"
                bat "flutter pub get" 
            }
        }

        stage('Build APK') {
            steps {
                bat "flutter build apk"
            }
        }
    }
}