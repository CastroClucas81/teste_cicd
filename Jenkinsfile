pipeline {
    agent any

    environment {
        FLUTTER_PATH = 'C:\\Users\\Usuario\\.puro\\envs\\stable\\flutter\\bin'
        PATH = '${FLUTTER_PATH};${env.PATH}'
    }

    stages {
        stage('Checkout') {
            steps {
                bat 'flutter --version' 
            }
        }
    }
}