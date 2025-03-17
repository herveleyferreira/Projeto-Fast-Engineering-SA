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

## Modernização com Kubernetes

### Objetivo da Etapa 2

A modernização envolve *migrar* a aplicação existente para *Kubernetes* no **Amazon EKS** e configurar os serviços auxiliares.

---

## Atividades Necessárias para a Migração

- **Análise e Planejamento**: Levantar requisitos de infraestrutura, segurança e escalabilidade.  
- **Criação do Cluster EKS**: Provisionar e configurar o **Amazon EKS** para ambiente de produção e desenvolvimento.  
- **Containerização das Aplicações**: Criar **Dockerfiles**, ajustar aplicações para rodar em contêineres e armazená-los no **Amazon ECR**.  
- **Configuração de Rede**: Definir **subnets**, **NAT Gateway**, **Internet Gateway** e **Security Groups**.  
- **Deploy de Serviços**: Criar manifests Kubernetes (**Deployment**, **Service**, **Ingress**) para frontend, backend e APIs.  
- **Banco de Dados**: Configurar **RDS Multi-AZ** para garantir alta disponibilidade.  
- **Balanceamento de Carga**: Utilizar **ALB (Application Load Balancer)** para distribuir o tráfego.  
- **Segurança**: Configurar **IAM**, **AWS WAF**, **AWS Shield**, **Secrets Manager** e monitoramento com **CloudWatch**.  
- **Backup e Disaster Recovery**: Definir estratégias de backup no **AWS Backup** e snapshots no RDS.  
- **Testes e Validação**: Testar desempenho, segurança e falhas antes de migrar o tráfego definitivamente.  

---

## Ferramentas que Serão Utilizadas

- **Orquestração de Contêineres**: Amazon EKS.  
- **Gerenciamento de Contêineres**: Docker e Amazon ECR.  
- **Rede e Segurança**: VPC, Security Groups, IAM, AWS WAF, AWS Shield, AWS Secrets Manager.  
- **Banco de Dados**: Amazon RDS Multi-AZ.  
- **Balanceamento de Carga**: ALB (Application Load Balancer).  
- **DNS e CDN**: Route 53 e AWS CloudFront.  
- **Monitoramento e Logging**: Amazon CloudWatch, AWS Backup.  
- **Armazenamento**: Amazon S3.  
- **Ferramentas Auxiliares**: AWS Organizations, AWS IAM.  

---

## Diagrama da Infraestrutura na AWS

![diagrama_kubernetes](https://github.com/user-attachments/assets/9a1eeeef-8179-4a11-bff7-9c9d487d4ee7)

## Descrição do Diagrama

### Ambientes
- Dois ambientes isolados (**DEV** e **PROD**) em **VPCs separadas**.

### Orquestração de Contêineres
- **Amazon EKS** para gerenciar workloads em Kubernetes.

### Computação
- Três nós **EC2** para o cluster Kubernetes, cada um com **4 vCPUs** e **10GB de RAM**.

### Banco de Dados
- **Amazon RDS Multi-AZ** com três nós (1 primário + 2 réplicas) para alta disponibilidade.

### Armazenamento
- **Amazon S3** para persistência de objetos (imagens, logs etc.).
- **Amazon EBS** para volumes persistentes dos contêineres.

### Rede e Segurança
- **Subnets privadas** para banco de dados e backend, **públicas** para frontend e balanceadores.
- **NAT Gateway** para comunicação de instâncias privadas com a internet.
- **AWS WAF** e **AWS Shield** para proteção contra ataques.
- **VPN** para acesso seguro dos desenvolvedores.

### Balanceamento de Carga
- **Application Load Balancer (ALB)** distribuindo tráfego para o EKS.

### DNS e CDN
- **Route 53** para gerenciamento de domínios.
- **CloudFront** para distribuição de conteúdo.

### Monitoramento e Gestão
- **CloudWatch** para logs e métricas.
- **AWS Backup** para snapshots automáticos.

---

## Requisitos de Segurança

- **Controle de Acesso**: IAM com permissões mínimas necessárias para cada serviço.  
- **Proteção contra Ataques**: AWS WAF para filtragem de tráfego malicioso, AWS Shield contra DDoS.  
- **Gerenciamento de Segredos**: AWS Secrets Manager para credenciais e chaves sensíveis.  
- **Redes Seguras**: Uso de subnets privadas para banco de dados e backend, acesso a partir de VPNs.  
- **Monitoramento e Logging**: CloudWatch para logs e métricas, CloudTrail para auditoria.  
- **Criptografia**: Dados criptografados em trânsito (TLS) e em repouso (KMS no RDS e S3).  
- **Backup e Disaster Recovery**: AWS Backup e snapshots automáticos no RDS.  

---

## Processo de Backup

- **Banco de Dados**: Snapshots automáticos no Amazon RDS com retenção configurável.  
- **Armazenamento de Objetos**: Amazon S3 versionado e com políticas de ciclo de vida.  
- **Volumes de Armazenamento**: Backup via AWS Backup para snapshots de EBS.  
- **Configuração e Logs**: Logs armazenados no CloudWatch e replicação para S3.  

---

## Custo da Infraestrutura na AWS



## Conclusão

A migração e modernização da infraestrutura do nosso e-commerce para a AWS representam um **marco estratégico** para garantir escalabilidade, segurança e alta disponibilidade. Com a primeira etapa (**"Lift-and-Shift"**), replicamos a infraestrutura atual na AWS de forma rápida e segura, utilizando serviços como **EC2**, **RDS Multi-AZ**, **S3**, **ELB**, **WAF**, **Shield** e **Route 53**. Isso nos permitiu reduzir o risco de downtime, melhorar o desempenho e preparar o ambiente para a próxima fase.

Na segunda etapa, com a **modernização para Kubernetes no Amazon EKS**, avançaremos ainda mais, garantindo:
- **Escalabilidade automática**: Para lidar com picos de tráfego sem intervenção manual.
- **Resiliência**: Com a orquestração de contêineres, garantimos que a aplicação se recupere rapidamente de falhas.
- **Segurança reforçada**: Utilizando **IAM**, **AWS WAF**, **Shield** e **Secrets Manager**, protegemos dados sensíveis e aplicações contra ameaças.
- **Eficiência operacional**: Com a automação de deploys, monitoramento e backups, reduzimos a complexidade e os custos operacionais.

### Benefícios Esperados
- **Alta disponibilidade**: Com o RDS Multi-AZ e o ELB, garantimos que o site esteja sempre no ar, mesmo durante falhas ou ataques.
- **Segurança robusta**: Proteção contra DDoS, injeções de SQL, XSS e outras ameaças comuns.
- **Custo otimizado**: Utilizamos instâncias adequadas e estratégias de backup para evitar gastos desnecessários.
- **Preparação para o futuro**: A arquitetura na AWS e o uso de Kubernetes nos permitem escalar rapidamente e adotar novas tecnologias.

Com essa migração, estamos construindo uma base sólida para o crescimento contínuo do e-commerce, garantindo uma **experiência superior para os clientes** e uma **operação mais eficiente** para a equipe. O futuro é escalável, seguro e inovador! 🚀


