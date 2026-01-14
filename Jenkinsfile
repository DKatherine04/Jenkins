pipeline {
    agent any

    stages {

        stage('Verificar Node y Docker') {
            steps {
                bat 'node -v'
                bat 'npm -v'
                bat 'docker --version'
            }
        }

        stage('Instalar dependencias') {
            steps {
                bat 'npm install'
            }
        }

        stage('Construir imagen Docker') {
            steps {
                bat 'docker build -t hola-mundo-node:latest .'
            }
        }

        stage('Ejecutar contenedor') {
            steps {
                bat '''
                docker stop hola-mundo-node || exit 0
                docker rm hola-mundo-node || exit 0
                docker run -d --name hola-mundo-node -p 3000:3000 hola-mundo-node:latest
                '''
            }
        }
    }
}
