pipeline {
    agent any

    environment {
        DOCKER_IMAGE_FLASK = "flask_app_image"
        DOCKER_IMAGE_MARIADB = "mariadb_image"
    }

    stages {
        stage('Clonando repositório') {
            steps {
                echo 'Clonando repositório...'
                checkout scm
            }
        }

        stage('Aplicando testes') {
            steps {
                echo 'Testes unitários...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline concluída com sucesso.'
        }

        failure {
            echo 'Falha na Pipeline.'
        }
    }
}