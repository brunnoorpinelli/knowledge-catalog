# Demo — Google Cloud Knowledge Catalog

Demonstração prática do **Google Cloud Knowledge Catalog** (evolução do Dataplex Universal Catalog), o catálogo de dados do Google Cloud potencializado por Gemini, que funciona como um *universal context engine*: fornece contexto de negócio, governança e semântica para todo o data estate — para pessoas **e** para agentes de IA.

> ⚠️ Este repositório usa **apenas dados fictícios (fake)** gerados sinteticamente. Nenhuma informação de cliente ou dado confidencial é utilizada.

📖 Documentação oficial: [Introdução ao Knowledge Catalog](https://docs.cloud.google.com/dataplex/docs/introduction)
📰 Blog post de lançamento: [Introducing the Google Cloud Knowledge Catalog](https://cloud.google.com/blog/products/data-analytics/introducing-the-google-cloud-knowledge-catalog)

---

## O que é o Knowledge Catalog?

Anunciado no Google Cloud Next '26, o Knowledge Catalog evolui o Dataplex de um catálogo de dados tradicional para um **motor de contexto dinâmico e sempre ativo**, organizado em três pilares:

1. **Agregação** — unificar contexto de todo o data estate (Google Cloud, bancos third-party e catálogos parceiros);
2. **Enriquecimento** — geração contínua e automatizada de significado (descrições, glossários, relacionamentos) com Gemini;
3. **Busca/Recuperação** — retrieval de alta precisão e seguro, para usuários e agentes de IA (via MCP e APIs de contexto).

> A mudança de nome (abril/2026) não altera APIs, client libraries, CLI (`gcloud dataplex`) nem papéis IAM.

---

## Funcionalidades

### Descoberta e Catalogação

- **Descoberta e ingestão automática de metadados** — harvesting automático de metadados técnicos de BigQuery, AlloyDB, Spanner, Cloud SQL, Firestore (Preview), Pub/Sub, Cloud Storage, Vertex AI, Looker (Preview), Dataform e catálogos Iceberg REST; além de fontes third-party via conectores. [Docs](https://docs.cloud.google.com/dataplex/docs/discover-data)
- **Conectividade gerenciada e conectores third-party** — pipelines de conectividade gerenciada para importar metadados de Oracle, MySQL, PostgreSQL, SQL Server e outros sistemas externos. [Docs](https://docs.cloud.google.com/dataplex/docs/managed-connectivity-overview)
- **Busca semântica de alta precisão (GA)** 🆕 — stack híbrido baseado em tecnologia do Google Search (query rewriting + ML), com latência subsegundo, busca em linguagem natural, filtros facetados e operadores lógicos. A busca respeita permissões dos sistemas de origem (*access control-aware search*). [Docs](https://docs.cloud.google.com/dataplex/docs/search-assets)

### Enriquecimento de Metadados e Contexto de Negócio

- **Aspects e tags (metadados customizados)** — enriquecimento de entradas do catálogo com metadados estruturados customizados, incluindo descrições geradas por IA. [Docs](https://docs.cloud.google.com/dataplex/docs/enrich-entries-metadata)
- **Glossário de negócio** — definição centralizada de terminologia de negócio, com associação de termos a colunas/tabelas e import/export via JSON e Google Sheets. [Docs](https://docs.cloud.google.com/dataplex/docs/manage-glossaries)
- **Curadoria automática de contexto (Preview)** 🆕 — Gemini gera automaticamente descrições em linguagem natural, glossários de negócio, relacionamentos e padrões de SQL verificados, inferindo relações ocultas em um mapa de negócio evolutivo.
- **Relacionamentos entre dados (Preview)** 🆕 — descoberta automática de relacionamentos entre tabelas via análise de logs de consulta (padrões de `JOIN`) e via *data insights* (análise de schema com LLMs). Alimenta agentes de IA com contexto estrutural para gerar queries precisas. [Docs](https://docs.cloud.google.com/dataplex/docs/data-relationships)
- **Extração multimodal profunda de metadados (Preview)** 🆕 — integração nativa com Gemini para extrair entidades e mapear relacionamentos de negócio a partir de conteúdo não estruturado (ex.: PDFs no Cloud Storage). [Docs](https://docs.cloud.google.com/dataplex/docs/data-insights-unstructured-data)
- **Smart Storage e Object Context API (Preview)** 🆕 — enriquecimento automático no Cloud Storage: arquivos são tagueados, indexados e enriquecidos com metadados no momento do upload, tornando dados não estruturados imediatamente descobríveis por agentes.

### Contexto para IA (AI Grounding)

- **Servidores MCP e APIs de recuperação de contexto** 🆕 — o catálogo serve contexto empresarial a agentes de IA via Model Context Protocol (local e remoto) e APIs como `LookupContext`, reduzindo alucinações. [Docs](https://docs.cloud.google.com/dataplex/docs/mcp-overview)
- **Queries verificadas e guardrails semânticos (Preview)** 🆕 — padrões de SQL verificados e perguntas em linguagem natural pré-geradas, evitando lógica alucinada e `JOIN`s "adivinhados" por agentes.
- **Context Graph** 🆕 — mapa dinâmico conectando schemas técnicos, entidades de negócio e conhecimento não estruturado, construído pelo Gemini a partir de schemas, logs de consulta e modelos semânticos.
- **BigQuery measures + LookML (Preview)** 🆕 — lógica de negócio programática embutida no engine SQL, unificada com LookML em uma única fundação semântica governada.

### Governança e Qualidade

- **Data lineage** — rastreamento e visualização automática de linhagem, busca multi-região, integração OpenLineage e linhagem de sistemas externos. Casos de uso: análise de impacto, rastreamento de PII e otimização de custos. [Docs](https://docs.cloud.google.com/dataplex/docs/about-data-lineage)
- **Auto data quality** — regras de qualidade reutilizáveis, templates de regras do sistema e *rules-as-code* via Terraform/Cloud Build/GitHub. [Docs](https://docs.cloud.google.com/dataplex/docs/auto-data-quality-overview)
- **Data profiling e insights** — profiling automatizado para identificar padrões e anomalias; geração de insights para dados estruturados e não estruturados. [Docs](https://docs.cloud.google.com/dataplex/docs/data-profiling-overview)
- **Data products (GA)** 🆕 — empacotamento de ativos de dados com metadados, scores de qualidade, linhagem, SLAs e restrições de governança em produtos curados — blocos de construção para agentes de IA em produção. [Docs](https://docs.cloud.google.com/dataplex/docs/data-products-overview)
- **Segurança e controle de acesso** — IAM, VPC Service Controls, CMEK e constraints customizadas de organization policy. [Docs](https://docs.cloud.google.com/dataplex/docs/iam-and-access-control)
- **Monitoramento e change feeds** — logs de jobs, audit logging, métricas e notificações de mudança de metadados. [Docs](https://docs.cloud.google.com/dataplex/docs/metadata-change-feeds-overview)

🆕 = novidade anunciada no [blog post do Knowledge Catalog](https://cloud.google.com/blog/products/data-analytics/introducing-the-google-cloud-knowledge-catalog) (Google Cloud Next '26).

---

## Escopo da demo

Este repositório conterá um notebook do **Colab Enterprise** demonstrando, com dados fictícios:

1. **Criação de tabelas fake** no BigQuery (dados sintéticos, sem qualquer informação real);
2. **Geração de documentação** para o catálogo (descrições de tabelas e colunas);
3. **Glossário de negócio** — criação de glossário, termos e associação a ativos de dados;
4. **Relacionamento de tabelas** — descoberta e consulta de [data relationships](https://docs.cloud.google.com/dataplex/docs/data-relationships) entre as tabelas da demo;
5. **Conversational Analytics** — chat em linguagem natural com os dados do BigQuery, ancorado (AI grounding) no contexto do catálogo: descrições, glossário e relacionamentos.

## Pré-requisitos

- Projeto no Google Cloud com billing habilitado;
- APIs habilitadas: `dataplex.googleapis.com`, `bigquery.googleapis.com`, `datacatalog.googleapis.com`;
- Permissões IAM adequadas no projeto (ex.: `roles/dataplex.admin`, `roles/bigquery.admin` — apenas para ambiente de demo);
- Acesso ao Colab Enterprise (Vertex AI).

## Aviso

Projeto de demonstração, sem vínculo oficial com o Google. Todos os dados são sintéticos. Funcionalidades marcadas como *Preview* estão sujeitas aos [Pre-GA Offerings Terms](https://cloud.google.com/terms/service-terms).
