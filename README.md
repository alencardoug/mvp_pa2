# RAGFlow com ElasticSearch

Projeto prático de AI Engineering focado na construção e avaliação de uma arquitetura corporativa de Retrieval-Augmented Generation (RAG) para um cenário simulado de atendimento em saúde.

O projeto foi desenvolvido principalmente como ambiente de aprendizado e experimentação para compreender os componentes necessários para tornar uma solução RAG mais confiável, rastreável e sustentável em um contexto próximo de produção.

## Objetivos

O objetivo principal não é apenas fazer um LLM responder perguntas a partir de documentos, mas explorar as decisões de engenharia por trás de uma solução RAG robusta.

O projeto aborda:

- **RAGFlow** como principal plataforma de RAG e camada de orquestração.
- **Elasticsearch** para indexação e recuperação escalável de documentos.
- **Busca híbrida**, combinando similaridade semântica/vetorial com busca lexical.
- **Embeddings** e seu impacto na qualidade da recuperação de documentos.
- **Estratégias de chunking**, incluindo experimentos com tamanho dos chunks, estrutura documental e limites semânticos.
- **Estruturas parent-child** para preservar contexto mantendo unidades de recuperação mais precisas.
- **Avaliação de recuperação**, verificando se os chunks corretos são recuperados antes mesmo de avaliar a resposta final do LLM.
- **Ajustes de similaridade e ranking**, entendendo como parâmetros de recuperação afetam precisão e recall.
- **Filtros por metadados** para melhorar buscas contextuais e específicas por domínio.
- **PostgreSQL** para dados estruturados, governança, rastreabilidade e informações determinísticas da aplicação.
- **Workflows determinísticos** para operações que não devem depender de IA generativa, como ações estruturadas de negócio.
- **RAG vs. lógica determinística**, identificando quando uma informação deve vir da recuperação semântica e quando deve ser tratada pela aplicação tradicional.
- **LangChain** para integração e orquestração em nível de aplicação.
- **LangGraph** para workflows de IA explícitos, com estado e maior controle.
- Conceitos de **LangSmith / Langfuse** para tracing, observabilidade, depuração e avaliação das execuções de IA.
- **Docker Compose** para uma infraestrutura local reproduzível.
- **Otimização de recursos**, executando a stack em um ambiente local com recursos limitados.
- Conceitos de **deploy em nuvem**, preparando a arquitetura para uma futura implantação no GCP.
- **Governança e rastreabilidade em RAG**, mantendo fontes recuperadas e decisões do sistema auditáveis.
- **Arquitetura orientada à segurança**, especialmente relevante para aplicações corporativas e relacionadas à saúde.

## Arquitetura

Em alto nível:

```text
Documentos
    │
    ▼
 RAGFlow
    │
    ├── Chunking / Parsing
    ├── Embeddings
    └── Metadados
    │
    ▼
Elasticsearch
    │
    ├── Busca Vetorial
    ├── Busca por Palavras-chave
    └── Recuperação Híbrida
    │
    ▼
Aplicação / Workflow de IA
    │
    ├── LangChain
    ├── LangGraph
    ├── Regras Determinísticas
    └── LLM
    │
    ▼
Resposta Rastreável
```

O PostgreSQL complementa a camada de RAG armazenando dados estruturados da aplicação e informações que não devem depender de recuperação semântica.

## Domínio de Exemplo

O cenário demonstrativo simula uma base de conhecimento corporativa para atendimento em saúde, com temas como:

- reagendamento de consultas;
- documentos necessários;
- orientações de preparo;
- informações administrativas;
- procedimentos de atendimento ao paciente.

O projeto utiliza apenas informações sintéticas ou demonstrativas e não se destina a decisões clínicas reais.

## Principal Aprendizado

Um dos principais aprendizados deste projeto é que **a qualidade de uma solução RAG depende fortemente da qualidade da recuperação**.

Um LLM poderoso não consegue compensar de maneira confiável documentos mal estruturados, chunking inadequado, embeddings fracos ou um ranking de recuperação incorreto.

Por isso, o projeto trata os testes de retrieval como uma atividade central de engenharia, em vez de avaliar apenas a resposta final gerada pelo modelo.

## Status

🚧 **Projeto de aprendizado e portfólio — em desenvolvimento ativo**

Os experimentos atuais incluem infraestrutura local com RAGFlow, recuperação com Elasticsearch, chunking de documentos, similaridade de embeddings e validação de retrieval.

As próximas iterações expandem a solução para orquestração da aplicação, observabilidade, avaliação, workflows determinísticos, governança e deploy em nuvem.

## Propósito

Este repositório faz parte do meu portfólio de AI Engineering e tem como objetivo demonstrar conhecimento prático em:

**RAG · AI Engineering · Retrieval · Elasticsearch · RAGFlow · LangChain · LangGraph · Observabilidade de LLMs · Engenharia de Dados · GCP**
