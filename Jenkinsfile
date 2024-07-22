pipeline {
    agent any

    environment {
        ANDROID_HOME = "C:\\Users\\Usuario\\AppData\\Local\\Android\\Sdk"
        FLUTTER_HOME = "C:\\Users\\Usuario\\.puro\\envs\\stable\\flutter"
        FLUTTER_PATH = "${FLUTTER_HOME}\\bin"
        PATH = "${FLUTTER_HOME};${FLUTTER_PATH};${ANDROID_HOME};${env.PATH}"
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
                    cd ./android
                    ./gradlew clean build
                    flutter build apk
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