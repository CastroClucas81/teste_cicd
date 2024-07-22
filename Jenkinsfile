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
                sh "flutter pub get" 
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
                    flutter clean
                    flutter build apk --release --verbose

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