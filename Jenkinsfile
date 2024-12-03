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
                script {
                    try {
                        sh '''
                            python3 -m venv venv
                            . venv/bin/activate
                            pip install -r flask/requirements.txt
                            FLASK_ENV=testing python -m unittest discover -s flask -p "test_*.py"
                        '''
                    } catch (Exception e) {
                        echo "Erro ao rodar os testes: ${e.getMessage()}"
                        error "Falha nos testes unitários."
                    }
                }
            }
        }

        stage('Cleanup Docker Resources') {
            steps {
                script {
                    try {
                        sh '''
                            # Stop all running containers
                            docker stop $(docker ps -a -q) || true
                            
                            # Remove all containers
                            docker rm -f $(docker ps -a -q) || true
                            
                            # Remove all volumes
                            docker volume prune -f
                            
                            # Remove all networks
                            docker network prune -f
                        '''
                    } catch (Exception e) {
                        echo "Erro na limpeza de recursos Docker: ${e.getMessage()}"
                    }
                }
            }
        }

        stage('Build de Imagens Docker') {
            steps {
                echo 'Criando imagens Docker...'
                script {
                    try {
                        sh '''
                            docker-compose build
                        '''
                    } catch (Exception e) {
                        echo "Erro ao criar as imagens Docker: ${e.getMessage()}"
                        error "Falha no build das imagens Docker."
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Fazendo deploy da aplicação...'
                script {
                    try {
                        sh '''
                            docker-compose up -d
                        '''
                    } catch (Exception e) {
                        echo "Erro ao realizar o deploy: ${e.getMessage()}"
                        error "Falha no deploy da aplicação."
                    }
                }
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