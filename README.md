# Trabalho_DevOps_0482941
- Camila Zambrana de Macedo Specalski

## Sistema de Gerenciamento de Alunos - Projeto DevOps

## 📝 Descrição do Projeto

Este projeto é uma aplicação web desenvolvida para demonstrar práticas modernas de DevOps, focando na integração contínua, implantação automatizada e monitoramento de uma aplicação de gerenciamento de alunos.

## 🛠 Tecnologias Utilizadas

- **Linguagem**: Python
- **Framework Web**: Flask
- **Containerização**: Docker
- **Orquestração**: Docker Compose
- **CI/CD**: Jenkins
- **Monitoramento**: 
  - Prometheus
  - Grafana
- **Banco de Dados**: MariaDB
- **Controle de Versão**: Git

## 🌐 Portas do Ambiente

| Serviço    | Porta | Descrição                      |
|------------|-------|--------------------------------|
| Aplicação  | 5000  | Servidor Flask                 |
| Jenkins    | 8080  | Servidor de Automação          |
| Grafana    | 3000  | Painel de Visualização         |
| Prometheus | 9090  | Monitoramento de Métricas      |
| MariaDB    | 3306  | Banco de Dados                 |

## 🔧 Pré-requisitos

- Docker
- Docker Compose
- Jenkins
   Git

## 🚀 Configuração e Instalação

### Passos para Configuração:

1. **Clonar o Repositório**
   ```bash
   git clone https://github.com/CamilaZMS/Trabalho_DevOps_0482941
   cd devops-project
   ```

2. **Configurar Jenkins**
   - Acesse `http://localhost:8080`
   - Instale os plugins necessários
   - Crie uma nova pipeline

3. **Configurar Pipeline**
   - Tipo: Pipeline
   - SCM: Git
   - Repositório: `https://github.com/CamilaZMS/Trabalho_DevOps_0482941`
   - Branch: `main`

4. **Construir e Executar**
Faça login no Jenkins em http://localhost:8080
Localize a pipeline criada (por exemplo, Pipeline-Alunos)
Clique em "Construir Agora" (ou "Build Now")
Monitore a execução:

Acompanhe os logs para verificar:

Clonagem do repositório
Execução de testes
Build de imagens Docker
Deploy dos serviços




Verifique o status final da pipeline:

## 📊 Dashboard de Métricas

O projeto inclui um dashboard Grafana personalizado com duas métricas principais:

### 1. Web Application Accesses
- **Métrica**: `rate(flask_http_request_total[1m])`
- **Descrição**: Taxas de requisições HTTP da aplicação Flask
- **Visualização**: Gráfico de série temporal
- **Cores**: 
  - Verde padrão
  - Vermelho para valores acima de 80 requisições

### 2. Database Queries
- **Métrica**: `rate(mysql_global_status_questions[1m])`
- **Descrição**: Taxas de consultas no banco de dados MariaDB
- **Visualização**: Gráfico de série temporal
- **Cores**: 
  - Azul claro padrão
  - Rosa para valores acima de 80 consultas

### Detalhes Técnicos do Dashboard
- **Período de Visualização**: Últimos 5 minutos
- **Atualização**: Tempo real
- **Ferramentas**: Prometheus + Grafana
- **Versão do Dashboard**: 12

## 🔍 Acessando Serviços

| Serviço | URL                  
|---------|----------------------
| Grafana | `http://localhost:3000` 
| Jenkins | `http://localhost:8080` 
| Aplicação | `http://localhost:5000`

## 🚨 Observações

- Certifique-se de ter todas as dependências instaladas
- Recomenda-se uso em ambiente Linux

---
