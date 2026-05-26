# 🗓️ Cronograma de Estudos Detalhado

Este documento contém o roteiro prático passo a passo de **30 dias (4 semanas)** para sua jornada no desenvolvimento backend. Cada semana tem um foco estratégico, metas teóricas e, o mais importante, **desafios práticos** para solidificar o conhecimento.

---

## 🎯 Semana 1: Fundamentos de APIs REST e Arquitetura
**Foco:** Dominar a base sólida de como os serviços se comunicam na web e projetar APIs limpas e padronizadas.

### 📅 Dia 1-2: Fundamentos de HTTP e REST
*   **Conceitos Chave:**
    *   **Verbos HTTP:** Compreender o uso semântico de `GET`, `POST`, `PUT`, `DELETE` e `PATCH`.
    *   **Códigos de Status:** Entender as famílias de respostas HTTP (`2xx` Sucesso, `3xx` Redirecionamento, `4xx` Erro do Cliente, `5xx` Erro do Servidor).
    *   **RESTful Core:** O que significa ser *Stateless*, o conceito de *Resources* e URIs bem desenhadas.
*   **🛠️ Atividade Prática:**
    *   Desenhar um diagrama de fluxo de dados/relação para uma API simples de CRUD (ex: CRUD de usuários com entidades Perfil e Cargo). Planeje os endpoints e o comportamento das requisições e respostas.

### 📅 Dia 3-4: Design de APIs
*   **Conceitos Chave:**
    *   **Versionamento:** Decidir entre versionamento na URI (ex: `/api/v1/...`) vs Header (`Accept: application/vnd.company.v1+json`).
    *   **Tratamento de Erros e Logs:** Estruturar respostas de erro amigáveis (ex: padrão RFC 7807) e entender onde/como gerar logs importantes.
    *   **Autenticação Básica:** Compreender o fluxo de chaves de API (*API Keys*), tokens opacos e a introdução teórica a OAuth2 e JWT.
*   **🛠️ Atividade Prática:**
    *   Escrever a especificação OpenAPI (Swagger) no formato YAML ou JSON para uma API fictícia usando o [Swagger Editor](https://editor.swagger.io/). Documente pelo menos 3 endpoints e suas respostas de erro.

### 📅 Dia 5-7: Mão na Massa (API Simples)
*   **Conceitos Chave:**
    *   Implementação prática de rotas, conexão com banco de dados e serialização de dados.
*   **🛠️ Atividade Prática:**
    *   Escolha sua linguagem de preferência (Java/Spring Boot, Node.js, Python, Go).
    *   Crie uma API RESTful funcional conectada a um banco de dados (pode ser em memória como H2, ou relacional/NoSQL local como PostgreSQL, MySQL ou MongoDB).
    *   Configure e realize requisições de teste utilizando ferramentas como **Postman**, **Insomnia** ou a extensão REST Client do VS Code.

---

## 🐳 Semana 2: Containerização com Docker
**Foco:** Garantir consistência. Empacotar sua aplicação e banco de dados para rodar de forma idêntica em qualquer ambiente (desenvolvimento, homologação e produção).

### 📅 Dia 8-9: Conceitos de Containers vs VMs
*   **Conceitos Chave:**
    *   **Arquitetura Docker:** A diferença entre isolamento de contêineres (compartilhando o Kernel do SO) e virtualização completa (Hypervisor e SOs convidados).
    *   **Componentes:** O papel do Docker Engine, imagens, contêineres e o Docker Registry.
    *   **Primeiros Comandos:** Familiarizar-se com `docker run`, `docker ps`, `docker stop`, `docker images` e `docker logs`.

### 📅 Dia 10-12: Dockerfile e Imagens
*   **Conceitos Chave:**
    *   **Instruções do Dockerfile:** Dominar as diretivas `FROM`, `RUN`, `CMD`, `COPY`, `ENTRYPOINT`, `ENV` e `EXPOSE`.
    *   **Camadas (Layers):** Como o Docker armazena em cache as camadas e como otimizar a ordem das instruções para builds mais rápidos.
    *   **Boas Práticas:** Construção de imagens leves, utilizando imagens base enxutas (como distros baseadas em *Alpine Linux*) e o conceito de *Multi-stage builds*.
*   **🛠️ Atividade Prática:**
    *   Escrever um `Dockerfile` otimizado para a API desenvolvida na **Semana 1**. Fazer o build da imagem localmente e rodá-la em um contêiner expondo a porta correta.

### 📅 Dia 13-14: Docker Compose e Redes
*   **Conceitos Chave:**
    *   **Orquestração Local:** Definir múltiplos serviços em um único arquivo de configuração usando `docker-compose.yml`.
    *   **Redes no Docker:** Como os contêineres se comunicam usando nomes de serviços como DNS interno.
    *   **Persistência (Volumes):** Entender a natureza efêmera dos contêineres e como mapear volumes locais para persistir os dados do banco.
*   **🛠️ Atividade Prática:**
    *   Criar um arquivo `docker-compose.yml` que configure dois serviços interligados em uma rede isolada: 1) Sua API Backend (construída a partir do Dockerfile); 2) O Banco de Dados escolhido. Rode toda a infraestrutura local com o comando `docker compose up`.

---

## ✉️ Semana 3: Introdução a Microsserviços e Mensageria
**Foco:** Escalar a arquitetura, entender o desacoplamento de sistemas e implementar comunicação assíncrona baseada em eventos.

### 📅 Dia 15-16: Monólito vs Microsserviços
*   **Conceitos Chave:**
    *   **Arquiteturas:** As vantagens da simplicidade de um monólito vs. a escalabilidade de microsserviços.
    *   **Desafios Práticos:** Lidar com latência de rede, consistência eventual de dados (Teorema CAP) e complexidade de deploy distribuído.
    *   **Padrões de Design:** Entender a função de um *API Gateway* (porta de entrada única) e do *Service Discovery* (localização dinâmica de serviços).

### 📅 Dia 17-19: Mensageria (Message Brokers)
*   **Conceitos Chave:**
    *   **Comunicação Baseada em Filas:** Por que usar filas para processamento assíncrono? Foco em resiliência, buffering e desacoplamento temporário.
    *   **Vocabulário de Eventos:** Compreender o papel de *Producer* (quem envia), *Consumer* (quem escuta), *Broker* (servidor de mensageria) e a diferença clássica entre *Filas* (Point-to-Point) e *Tópicos* (Publish/Subscribe).
    *   **Ferramentas:** Panorama geral sobre RabbitMQ (foco em roteamento avançado e filas AMQP) e Apache Kafka (foco em log de eventos de alto throughput e streaming).
*   **🛠️ Atividade Prática:**
    *   Instalar um broker local via Docker (RabbitMQ ou Kafka) e programar um script/serviço simples contendo um *Producer* que envia uma mensagem e um *Consumer* que processa essa mensagem simulando um "Pedido de Compra".

### 📅 Dia 20-21: Comunicação Síncrona vs Assíncrona
*   **Conceitos Chave:**
    *   **Tomada de Decisão:** Quando usar requisições síncronas (REST/gRPC) vs assíncronas (Mensageria/Eventos).
    *   **Transações Distribuídas:** Introdução teórica ao *Padrão Saga* (Sagas baseadas em Coreografia ou Orquestração) para manter a consistência entre diferentes serviços.
*   **🛠️ Atividade Prática:**
    *   Integrar a API desenvolvida na **Semana 1** com a fila criada. Ao receber uma requisição HTTP REST na API (ex: "Criar Pedido"), a API deve responder de forma rápida ao cliente enquanto publica uma mensagem na fila para que outro processo faça o processamento pesado de background.

---

## ☁️ Semana 4: Cloud e Deploy (O "Pulo do Gato")
**Foco:** Colocar sua aplicação no mundo real. Entender como funcionam os servidores em nuvem e automatizar o ciclo de entregas (CI/CD).

### 📅 Dia 22-23: Conceitos de Cloud Computing
*   **Conceitos Chave:**
    *   **Modelos de Serviço:** Compreender as diferenças práticas entre *IaaS* (Infraestrutura como Serviço), *PaaS* (Plataforma como Serviço) e *SaaS* (Software como Serviço).
    *   **Provedores Globais:** Visão geral dos três maiores players (AWS, Microsoft Azure, Google Cloud Platform).
    *   **Serviços Fundamentais:** Entender o conceito de instâncias de computação (EC2, Máquinas Virtuais), computação Serverless (AWS Lambda, Cloud Functions), bancos de dados gerenciados (RDS, Firestore) e armazenamento de objetos (S3, Cloud Storage).

### 📅 Dia 24-25: Estratégias de Deploy e CI/CD
*   **Conceitos Chave:**
    *   **Automação:** O risco de deploys manuais vs. a segurança de pipelines automatizados de Integração Contínua (CI) e Entrega Contínua (CD).
    *   **Conceito de Pipeline:** A jornada do código desde o commit inicial -> build da imagem -> execução de testes automatizados -> publicação da imagem -> deploy no servidor.
    *   **Ferramentas:** GitHub Actions ou GitLab CI (estrutura de arquivos `.github/workflows/*.yml`).

### 📅 Dia 26-28: Projeto Final Integrador
*   **🛠️ Desafio Prático Principal:**
    *   **Refatoração:** Revise e limpe o projeto integrado das Semanas 1, 2 e 3 (API REST conectada ao Banco + Mensageria).
    *   **Docker:** Certifique-se de que a API e dependências sobem perfeitamente via Docker Compose.
    *   **CI/CD:** Configure um pipeline básico no GitHub Actions que seja disparado a cada `git push` na branch principal para rodar os testes e buildar a imagem Docker.
    *   **Deploy na Nuvem:** Escolha um serviço PaaS gratuito ou de baixo custo (ex: Render, Railway, fly.io, ou camada gratuita da AWS/Azure) para hospedar a sua API pública e banco de dados.
    *   **Mensageria na Nuvem:** Conecte o projeto a um serviço de mensageria gerenciado na nuvem (ex: CloudAMQP para RabbitMQ gratuito ou AWS SQS).

### 📅 Dia 29-30: Revisão e Próximos Passos
*   **Conceitos Chave:**
    *   Revisar tópicos que se mostraram mais desafiadores durante o mês.
    *   **Olhar para o Futuro:** O que estudar a partir de agora? (Orquestradores de contêineres como Kubernetes, Infraestrutura como Código com Terraform, Observabilidade com Prometheus/Grafana/OpenTelemetry).
    *   **Portfólio:** Criar um belo arquivo README explicativo no repositório do seu projeto final no GitHub, incluindo diagramas de arquitetura, instruções de execução local e o link da API rodando em produção.

---

*(Dica: À medida que avança pelos dias, utilize o modelo de anotações em `/anotacoes/semana-01.md` para registrar seu diário de bordo!)*
