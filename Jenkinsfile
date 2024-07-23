pipeline {
    agent any

    environment {
        ANDROID_HOME = "C:\\Users\\Usuario\\AppData\\Local\\Android\\Sdk"
        PATH = "${ANDROID_HOME}\\tools;${ANDROID_HOME}\\platform-tools;${ANDROID_HOME};${env.PATH}"
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
                sh "flutter doctor -v" 
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
                   flutter build appbundle
                '''
            }
        }
    }

                    //  flutter build apk --release

    post {
        always {
            echo 'Pipeline finalizada.'
            cleanWs()
        }
        success {
            echo 'Build foi bem-sucedido!'
        }
        failure {
            echo 'Build falhou.'
        }
    }
}