pipeline {
    agent any

    environment {
        FLUTTER_PATH = "C:\\Users\\Usuario\\.puro\\envs\\stable\\flutter\\bin"
        PATH = "${FLUTTER_PATH};${env.PATH}"
    }

    stages {
        stage('Clone Repository') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/CastroClucas81/teste_cicd.git']]])
            }
        }

        stage('Checkout') {
            // steps {
            //     echo "${env.PATH}"
            //     bat "flutter --version" 
            // }
             steps {
                dir('C:\\Users\\Usuario\\.puro\\envs\\stable\\flutter\\bin') {
                    bat 'flutter --version'
                }
            }
        }
    }
}