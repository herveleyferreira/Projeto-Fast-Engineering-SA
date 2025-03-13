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
