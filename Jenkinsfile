pipeline {
    agent any
    
    stages {
        stage('Clonando repositório') {
            steps {
                echo 'Clonando repositório'
            }
        }

        stage('Instalar dependências') {
            steps {
                echo 'Instalando dependência'
            }
        }

        stage('Build') {
            steps {
                echo 'Build'
            }
        }
        
        stage('Testes unitários') {
            steps {
                echo 'Rodando testes unitários'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Build'
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploy"
            }
        }
        
        stage('Verificar status dos serviços') {
            steps {
                echo "Verificando status dos serviços"
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