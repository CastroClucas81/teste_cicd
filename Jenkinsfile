pipeline {
    agent any

    environment {
        ANDROID_HOME = "C:\\Users\\Usuario\\AppData\\Local\\Android\\Sdk"
        GRADLE_HOME = "C:\\Windows\\System32\\config\\systemprofile\\.gradle\\caches\\transforms-3\\cf73cc8a4ba953430926b62a90018a2f\\transformed\\core-1.6.0\\res\\drawable-mdpi-v4\\notification_bg_normal.9.png"
        PATH = "${ANDROID_HOME};${GRADLE_HOME};${env.PATH}"
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
                   flutter build apk --release
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizada.'
            cleanWs deleteDirs: true, notFailBuild: true
        }
        success {
            echo 'Build foi bem-sucedido!'
        }
        failure {
            echo 'Build falhou.'
        }
    }
}