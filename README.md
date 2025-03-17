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

## Migração "Lift-and-Shift" (As-Is)

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
     - Requisitos de segurança (controle de acesso, proteção contra ataques, etc.).

### 2. Configuração do Ambiente AWS
   - **Criação do VPC (Virtual Private Cloud)**:
     - Definição de sub-redes públicas e privadas.
     - Configuração de rotas e tabelas de roteamento.
   - **Configuração de Security Groups**:
     - Regras de firewall para controlar o tráfego de entrada e saída.
     - Restrição de acesso às instâncias EC2 e ao RDS.

### 3. Migração dos Servidores
   - **Migração do Frontend (React)**:
     - Utilização do **AWS Server Migration Service (SMS)** para migrar o servidor frontend para uma instância EC2.
     - Configuração do ambiente de execução (Node.js, Nginx, etc.).
   - **Migração do Backend (APIs)**:
     - Utilização do **AWS Server Migration Service (SMS)** para migrar o servidor backend para instâncias EC2.
     - Configuração do Nginx como balanceador de carga.
   - **Configuração do Elastic Load Balancer (ELB)**:
     - Distribuição do tráfego entre as instâncias do backend.

### 4. Migração do Banco de Dados
   - **Migração do MySQL para o Amazon RDS**:
     - Criação de uma instância RDS Multi-AZ para alta disponibilidade.
     - Uso do **AWS Database Migration Service (DMS)** para migração dos dados.
     - Configuração de backups automáticos no RDS.

### 5. Configuração de Segurança
   - **AWS WAF (Web Application Firewall)**:
     - Integrado ao Elastic Load Balancer (ELB) para proteção contra ataques web.
     - Configuração de regras personalizadas para bloquear tráfego malicioso.
   - **AWS Shield Standard**:
     - Proteção contra ataques DDoS.
     - Implementado em segundo plano para proteger o ELB e outros recursos públicos.

### 6. Configuração de Backup
   - **AWS Backup**:
     - Backup automatizado das instâncias EC2 e do RDS.
     - Configuração de políticas de retenção (7 dias para backups diários).
   - **Versionamento no S3**:
     - Habilitado para manter histórico de alterações nos arquivos estáticos.

### 7. Testes e Validação
   - **Testes de Carga**:
     - Uso do Apache JMeter para simular tráfego intenso e validar a escalabilidade.
   - **Testes Funcionais**:
     - Verificação do funcionamento do frontend, backend e banco de dados.
   - **Monitoramento com Amazon CloudWatch**:
     - Configuração de dashboards para monitorar métricas de desempenho (CPU, memória, tráfego, etc.).
     - Configuração de alertas para identificar problemas rapidamente.

### 8. Corte (Cutover)
   - **Atualização dos Registros DNS**:
     - Utilização do **Amazon Route 53** para redirecionar o tráfego para o novo ambiente na AWS.
     - Configuração de registros DNS para apontar para o Elastic Load Balancer (ELB).
   - **Monitoramento Pós-Migração**:
     - Uso do AWS CloudWatch para monitorar métricas e logs.
     - Configuração de alertas para identificar problemas rapidamente.

---

## Ferramentas Utilizadas

As seguintes ferramentas e serviços da AWS foram utilizados durante a migração:

1. **AWS Server Migration Service (SMS)**:
   - Utilizado para migração dos servidores (frontend e backend) para instâncias EC2.

2. **Amazon RDS**:
   - Utilizado para migração do banco de dados MySQL.
   - Configuração de uma instância RDS Multi-AZ para alta disponibilidade.

3. **Amazon S3**:
   - Utilizado para armazenamento de objetos estáticos (fotos, vídeos, links).

4. **AWS WAF (Web Application Firewall)**:
   - Proteção contra ataques web, como SQL Injection e XSS.

5. **AWS Shield Standard**:
   - Proteção contra ataques DDoS.

6. **AWS Backup**:
   - Utilizado para backups automatizados das instâncias EC2 e do RDS.

7. **Amazon CloudWatch**:
   - Utilizado para monitoramento de desempenho e logs.

8. **AWS CLI (Command Line Interface)**:
   - Utilizado para automação de tarefas, como criação de instâncias EC2 e gerenciamento de backups.

9. **Amazon Route 53**:
   - Utilizado para gerenciamento de DNS e redirecionamento do tráfego para o novo ambiente na AWS.

---

## Diagrama da Infraestrutura na AWS

Abaixo está o diagrama da infraestrutura na AWS após a migração "Lift-and-Shift":

![Migração Lift-and-Shift drawio](https://github.com/user-attachments/assets/e2c832e9-562f-4f2d-8b2f-66f0157c9a25)

### Descrição do Diagrama:
1. **Amazon Route 53**:
   - Serviço de DNS utilizado para redirecionar o tráfego externo para o Elastic Load Balancer (ELB).

2. **Frontend (React)**:
   - Hospedado em uma instância EC2.
   - Acesso público via Elastic Load Balancer (ELB).

3. **Backend (APIs + Nginx)**:
   - Hospedado em instâncias EC2.
   - Balanceamento de carga via ELB.
   - Arquivos estáticos armazenados no Amazon S3.

4. **Banco de Dados (MySQL)**:
   - Hospedado no Amazon RDS (Multi-AZ para alta disponibilidade).

5. **Armazenamento de Arquivos Estáticos**:
   - Bucket Amazon S3 para fotos, vídeos e links.

6. **Segurança**:
   - **AWS WAF**: Integrado ao ELB para proteção contra ataques web.
   - **AWS Shield Standard**: Proteção contra DDoS (representado como uma camada de proteção ao redor do ELB).
   - Grupos de segurança (Security Groups) para controlar o tráfego.
   - IAM para gerenciamento de permissões.

---

## Requisitos de Segurança

Para garantir a segurança do ambiente na AWS, foram implementadas as seguintes práticas:

1. **IAM (Identity and Access Management)**:
   - Criação de usuários e roles com permissões mínimas necessárias.
   - Uso de políticas de segurança restritivas.

2. **Grupos de Segurança (Security Groups)**:
   - Configuração de regras de firewall para permitir apenas tráfego necessário.
   - Bloqueio de portas não utilizadas.

3. **Proteção Contra Ataques**:
   - **AWS WAF**: Para proteção contra vulnerabilidades web.
   - **AWS Shield Standard**: Para proteção contra DDoS.

---

## Processo de Backup

O processo de backup foi configurado da seguinte forma:

1. **Banco de Dados (RDS)**:
   - Backups automáticos diários com retenção de 7 dias.
   - Snapshots manuais antes de grandes atualizações.

2. **Arquivos Estáticos (S3)**:
   - Versionamento habilitado no bucket S3 para manter histórico de alterações.
   - Configuração de Lifecycle Policies para armazenamento de backups em S3 Glacier.

3. **Instâncias EC2**:
   - Backup automatizado usando o AWS Backup.

---

## Custo da Infraestrutura na AWS

![file_2025-03-17_19 14 25](https://github.com/user-attachments/assets/8a0fde4d-3bc8-4775-9e98-ee11a52368b0)


