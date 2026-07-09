pipeline {
    agent any

    environment {
        DOCKER_API_VERSION = '1.40'
    }

    tools {
        dockerTool 'Dockertool'
    }

    stages {

        stage('Descargar proyecto') {
            steps {
                checkout scm
            }
        }

        stage('Construir Imagen Docker') {
            steps {
                sh 'pwd'
                sh 'ls -la'
                sh 'docker build -t hola-mundo-node:latest .'
            }
        }

        stage('Ejecutar Contenedor Node.js') {
            steps {
                sh '''
                docker stop hola-mundo-node || true
                docker rm hola-mundo-node || true
                docker run -d --name hola-mundo-node -p 3000:3000 hola-mundo-node:latest
                '''
            }
        }
    }
}