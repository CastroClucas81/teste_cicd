pipeline {
    agent any

    environment {
        // FLUTTER_HOME = "C:\\Users\\Usuario\\.puro\\envs\\stable\\flutter"
        // FLUTTER_HOME = "C:\\Windows\\System32\\config\\systemprofile\\.puro\\envs\\stable\\flutter"
        // PURO = "C:\\Windows\\System32\\config\\systemprofile\\.puro\\envs\\stable\\flutter\\bin"
        ANDROID_HOME = "C:\\Users\\Usuario\\AppData\\Local\\Android\\Sdk"
        GIT = "C:\\Program Files\\Git\\cmd;C:\\Program Files\\Git\\bin"
        PATH = "C:\\src\\flutter;C:\\src\\flutter\\bin;${GIT};${ANDROID_HOME};${env.PATH}"
    }

    stages {
        stage('Clone Repository') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/CastroClucas81/teste_cicd.git']]])
            }
        }

        stage('Checkout') {
            steps {
                echo "${env.PATH}"
                sh "flutter.bat doctor" 
            }
        }

        stage('Tests') {
            steps {
                sh "flutter test" 
            }
        }

          stage('Build Android') {
            steps {
                sh '''
                    flutter doctor
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizada.'
        }
        success {
            echo 'Build foi bem-sucedido!'
        }
        failure {
            echo 'Build falhou.'
        }
    }
}