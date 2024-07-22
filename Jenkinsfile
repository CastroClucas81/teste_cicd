pipeline {
    agent any

    environment {
        ANDROID_HOME = "C:\\Users\\Usuario\\AppData\\Local\\Android\\Sdk"
        PATH = "${ANDROID_HOME};${env.PATH}"
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
                sh "git config --global --add safe.directory '*'"
                sh "flutter doctor" 
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
                    flutter pub get
                    flutter build apk --debug
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