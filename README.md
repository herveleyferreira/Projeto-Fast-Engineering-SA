# Migração de E-commerce para AWS: Projeto Fast Engineering S/A

## Contexto

Nós, da empresa **Fast Engineering S/A**, estamos enfrentando desafios com a infraestrutura atual do nosso e-commerce devido ao crescimento acelerado da demanda. Para resolver isso, buscamos a expertise da empresa terceira **TI SOLUÇÕES INCRÍVEIS** para modernizar nossa infraestrutura e migrar para a AWS (Amazon Web Services).

### Situação Atual

Atualmente, nossa infraestrutura é composta por:

- **Banco de Dados MySQL**:
  - 01 servidor dedicado
  - 500GB de dados
  - 10GB de RAM
  - 3 Core CPU

- **Frontend (React)**:
  - 01 servidor dedicado
  - 5GB de dados
  - 2GB de RAM
  - 1 Core CPU

- **Backend (APIs + Nginx)**:
  - 01 servidor dedicado
  - 5GB de dados
  - 4GB de RAM
  - 2 Core CPU
  - Nginx atuando como balanceador de carga e servindo arquivos estáticos (fotos, links, etc.)

### Objetivo do Projeto

O objetivo principal é modernizar a infraestrutura do e-commerce migrando para a AWS, seguindo as melhores práticas de arquitetura em nuvem. A nova arquitetura deve incluir:

- Ambiente Kubernetes
- Banco de dados gerenciado (PaaS e Multi-AZ)
- Sistema de backup de dados
- Solução para persistência de objetos (imagens, vídeos, etc.)
- Segurança robusta

### Estratégia de Migração

A migração será realizada em duas etapas:

1. **Migração "Lift-and-Shift" (As-Is)**:
   - Migração rápida da infraestrutura atual para a AWS, sem alterações significativas na arquitetura.

2. **Modernização para Kubernetes**:
   - Após a migração inicial, a infraestrutura será reestruturada para utilizar Kubernetes e outros serviços gerenciados da AWS.

# Migração de E-commerce para AWS - Etapa 1: Migração "Lift-and-Shift" (As-Is)

## Escopo Detalhado

A primeira etapa do projeto consiste em realizar uma migração **"Lift-and-Shift"** (também conhecida como migração **"As-Is"**), onde a infraestrutura atual do e-commerce será replicada na AWS sem alterações significativas na arquitetura. O objetivo é garantir uma migração rápida e segura, minimizando o tempo de inatividade (downtime) e preparando o ambiente para a segunda etapa de modernização.

### Objetivos da Etapa 1

1. Replicar a infraestrutura atual na AWS.
2. Garantir a continuidade das operações do e-commerce durante a migração.
3. Preparar o ambiente para a modernização na Etapa 2 (Kubernetes).

---

## Atividades Necessárias para a Migração

### 1. Análise e Planejamento
   - **Mapeamento da Infraestrutura Atual**:
     - Identificação dos servidores e serviços em uso:
       - Banco de Dados MySQL.
       - Frontend (React).
       - Backend (APIs + Nginx).
     - Análise das dependências entre os componentes.
   - **Definição de Requisitos**:
     - Requisitos de desempenho (latência, throughput, etc.).
     - Requisitos de segurança (criptografia, controle de acesso, etc.).

### 2. Configuração do Ambiente AWS
   - **Criação do VPC (Virtual Private Cloud)**:
     - Definição de sub-redes públicas e privadas.
     - Configuração de rotas e tabelas de roteamento.
   - **Configuração de Security Groups**:
     - Regras de firewall para controlar o tráfego de entrada e saída.
     - Restrição de acesso às instâncias EC2 e ao RDS.

### 3. Migração dos Servidores
   - **Migração do Frontend (React)**:
     - Criação de uma instância EC2 para hospedar o frontend.
     - Configuração do ambiente de execução (Node.js, Nginx, etc.).
   - **Migração do Backend (APIs)**:
     - Criação de instâncias EC2 para hospedar as APIs.
     - Configuração do Nginx como balanceador de carga.
   - **Configuração do Elastic Load Balancer (ELB)**:
     - Distribuição do tráfego entre as instâncias do backend.

### 4. Migração do Banco de Dados
   - **Migração do MySQL para o Amazon RDS**:
     - Criação de uma instância RDS Multi-AZ para alta disponibilidade.
     - Uso do **AWS Database Migration Service (DMS)** para migração dos dados.
     - Configuração de backups automáticos no RDS.

### 5. Configuração de Segurança
   - **Implementação do AWS WAF (Web Application Firewall)**:
     - Proteção contra ataques comuns, como SQL Injection e XSS.
   - **Configuração do AWS Shield**:
     - Proteção contra ataques DDoS.
   - **Criptografia**:
     - Criptografia em repouso para o RDS e S3.
     - Criptografia em trânsito usando HTTPS.

### 6. Configuração de Backup
   - **Configuração do AWS Backup**:
     - Backup automatizado das instâncias EC2 e do RDS.
     - Definição de políticas de retenção (7 dias para backups diários).
   - **Versionamento no S3**:
     - Habilitado para manter histórico de alterações nos arquivos estáticos.

### 7. Testes e Validação
   - **Testes de Carga**:
     - Uso do Apache JMeter para simular tráfego intenso e validar a escalabilidade.
   - **Testes Funcionais**:
     - Verificação do funcionamento do frontend, backend e banco de dados.
   - **Testes de Segurança**:
     - Validação das configurações de segurança (WAF, Shield, IAM).

### 8. Corte (Cutover)
   - **Atualização dos Registros DNS**:
     - Redirecionamento do tráfego para o novo ambiente na AWS.
   - **Monitoramento Pós-Migração**:
     - Uso do AWS CloudWatch para monitorar métricas e logs.
     - Configuração de alertas para identificar problemas rapidamente.

---
