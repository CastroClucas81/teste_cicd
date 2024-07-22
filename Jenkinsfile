pipeline {
    agent any

    environment {
        ANDROID_HOME = "C:\\Users\\Usuario\\AppData\\Local\\Android\\Sdk"
        FLUTTER_PATH = "C:\\Users\\Usuario\\.puro\\envs\\stable\\flutter\\bin"
        PATH = "${FLUTTER_PATH};${ANDROID_HOME};${env.PATH}"
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
                bat "flutter pub get" 
            }
        }

        stage('Tests') {
            steps {
                bat "flutter test" 
            }
        }

          stage('Build') {
            steps {
                bat 'flutter build apk --debug'
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