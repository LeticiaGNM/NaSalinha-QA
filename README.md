# NaSalinha — QA Testing

## Sobre o projeto

Este repositório reúne a documentação e os artefatos produzidos durante o desafio de Quality Assurance (QA) da Comp Júnior, cujo objetivo é avaliar a qualidade do sistema NaSalinha, identificar possíveis defeitos e verificar se o comportamento da aplicação está de acordo com os requisitos especificados.

O trabalho contempla o planejamento e a execução de testes, o registro de defeitos encontrados e a documentação dos resultados obtidos.

## Tecnologias e ferramentas

### Tecnologias do sistema

- **Frontend:** React 18 e Tailwind CSS.
- **Backend:** Node.js e Express.
- **Banco de dados:** PostgreSQL.
- **ORM:** Prisma.
- **Autenticação:** JWT.
- **Armazenamento de imagens:** Cloudinary.
- **Infraestrutura local:** Docker e Docker Compose.

### Ferramentas de QA

- **Git e GitHub:** versionamento do projeto e organização da documentação.
- **Navegador web:** execução de testes funcionais na interface.
- **Insomnia:** planejamento e execução de testes de API.
- **Docker:** execução local do sistema e consulta aos logs dos serviços.

## Como executar o projeto

### Pré-requisitos

- Git instalado.
- Docker e Docker Compose instalados.
- Acesso ao repositório do sistema NaSalinha.

### 1. Clonar o sistema

Clone o repositório do sistema NaSalinha e entre na pasta do projeto:

```bash
git clone https://github.com/Gustavohmmagalhaes/nasalinha-qa-challenge.git
cd nasalinha-qa-challenge
```

### 2. Configurar as variáveis de ambiente

Crie o arquivo `.env` do backend a partir do modelo disponibilizado:

```bash
cp backend/.env.example backend/.env
```

Preencha as variáveis necessárias para o ambiente local, incluindo as credenciais do Cloudinary e do serviço de e-mail de teste (Mailtrap), conforme a configuração das respectivas plataformas.

**Importante:** o arquivo `.env` contém credenciais privadas e não deve ser enviado ao GitHub.

### 3. Iniciar os serviços

Na pasta raiz do sistema, execute:

```bash
docker compose up --build -d
```

### 4. Preparar o banco de dados

Execute as migrações e a carga inicial de dados conforme as instruções do projeto:

```bash
docker compose exec backend npx prisma migrate dev --name init
docker compose exec backend npx prisma db seed
```

> Se as migrações já tiverem sido aplicadas, verifique o estado do banco antes de executar novamente o comando de migração.

### 5. Acessar o sistema

Com os serviços em execução, acesse:

- **Frontend:** http://localhost:3000
- **Backend:** http://localhost:5001

O funcionamento dos serviços pode ser verificado com:

```bash
docker compose ps
```

## Estratégia de testes

A estratégia de QA será baseada nos requisitos fornecidos para as três áreas centrais do NaSalinha.

### 1. Autenticação JWT e controle de acesso

Verificar o cadastro e a confirmação de contas, as restrições de login e as permissões de acesso conforme o perfil do usuário. Também será avaliado o armazenamento seguro de senhas.

### 2. Check-in por foto

Verificar o envio de imagens, a associação dos check-ins à temporada ativa, as restrições de frequência e reutilização de fotos, o fluxo de aprovação e rejeição e as permissões de acesso aos registros. Também será verificada a remoção dos arquivos temporários após o processamento.

### 3. Sistema de pontos e ranking

Verificar a atribuição e a atualização dos pontos, a consistência do saldo após a remoção de check-ins e a ordenação do ranking conforme a pontuação total.

### Tipos de teste

- **Testes funcionais:** verificar o comportamento do sistema pela interface, considerando cenários positivos e negativos.
- **Testes de API:** verificar os endpoints, as respostas HTTP, os dados retornados e as regras de negócio implementadas no backend.
- **Testes de regressão:** repetir testes relevantes após uma correção hipotética de defeito para verificar se outras funcionalidades continuam funcionando corretamente.

Serão planejados dois casos de teste por requisito, conforme as orientações do desafio, contemplando as três áreas centrais.

## Documentação e resultados

A documentação será organizada neste repositório, contemplando:

- **Casos de teste:** funcionalidade, cenário, tipo, passos de execução e resultado esperado.
- **Coleção de API:** requisições utilizadas nos testes, exportadas em formato JSON.
- **Relatórios de defeitos (Bug Reports):** descrição do problema, passos para reprodução, resultado esperado, resultado obtido, evidências e severidade.
- **Relatório final de testes:** quantidade de casos planejados e executados, resultados aprovados e reprovados e distribuição dos defeitos por severidade.

Os defeitos encontrados serão documentados com evidências, buscando manter a rastreabilidade entre requisitos, casos de teste e resultados.

## Status do projeto

**Etapa atual:** configuração do ambiente local e exploração inicial do sistema.

O planejamento detalhado dos casos de teste, a execução dos cenários e a documentação dos defeitos serão desenvolvidos progressivamente durante o desafio.
