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
                echo 'Rodando testes unitários...'
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install -r flask/requirements.txt
                FLASK_ENV=testing python -m unittest discover -s flask -p "test_*.py"
                '''
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