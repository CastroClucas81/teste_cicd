pipeline {
    agent any

    environment {
        ANDROID_HOME = "C:\\Users\\Usuario\\AppData\\Local\\Android\\Sdk"
        // FLUTTER_HOME = "C:\\Users\\Usuario\\.puro\\envs\\stable\\flutter"
        FLUTTER_HOME = "C:\\Windows\\System32\\config\\systemprofile\\.puro\\envs\\stable\\flutter"
        // PURO = "C:\\Windows\\System32\\config\\systemprofile\\.puro\\envs\\stable\\flutter\\bin"
        FLUTTER_PATH = "${FLUTTER_HOME}\\bin"
        PATH = "${ANDROID_HOME};${env.PATH}"
        // PATH = "${FLUTTER_HOME};${FLUTTER_PATH};${ANDROID_HOME};${PURO};${env.PATH}"
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
                sh "flutter pub get" 
            }
        }

        stage('Tests') {
            steps {
                sh "flutter test" 
            }
        }

          stage('Build Android') {
                                // flutter pub get
                    // flutter build apk
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