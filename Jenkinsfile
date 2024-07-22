pipeline {
    agent any

    environment {
        FLUTTER_PATH = 'C:\\Users\\Usuario\\.puro\\envs\\stable\\flutter\\bin'
        PATH = '${FLUTTER_PATH};${env.PATH}'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/seu_usuario/seu_repositorio.git'
            }
        }

        stage('Checkout') {
            steps {
                bat 'flutter' 
            }
        }
    }
}