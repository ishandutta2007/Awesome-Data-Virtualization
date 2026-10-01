# Awesome-Data-Virtualization

## Top Data Virtualization Platforms Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**

*Focused on Data Federation, Virtual Views, Semantic Layers & Cross-Source Query Engines*

**Last updated: September 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Data Virtualization**. These tools help organizations query data across disparate sources—databases, data lakes, warehouses, APIs—without physically moving or copying it, presenting a unified logical view for analytics and applications.



**Examples** include Denodo, Dremio, CData Virtuality, TIBCO Data Virtualization, Starburst, IBM Cloud Pak for Data, Cisco Information Server, AtScale, and Red Hat Data Virtualization (the category leaders).



**Open-source emphasis**: Data virtualization has a **mature and production-proven open-source ecosystem**. **Trino** is the de facto standard for distributed federated SQL, powering Starburst's commercial platform . **Teiid** (319 stars) provides a robust data virtualization system for heterogeneous data stores . **DVT (Data Virtualization Tool)** extends dbt Core with cross-engine federation using DuckDB as a local compute engine . **Apache Calcite** provides the query planning and optimization foundation. This section documents these production-grade solutions.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents



- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Denodo](https://www.denodo.com/)**  

  The leading enterprise data virtualization platform. Provides logical data warehouse, data fabric, and data services capabilities across 200+ data sources. Known for its query optimization engine and metadata layer for unified governance .



- **[Dremio](https://www.dremio.com/)**  

  Cloud-native lakehouse platform with zero-ETL data federation. Provides virtual datasets (VDS) that query data across S3, ADLS, GCS, databases, and file systems without copying. Uses Apache Arrow-based engine with **Autonomous Reflections** for automatic query acceleration . Supports Apache Iceberg natively. **Community Edition** free for self-managed deployment; Cloud from $0.20/credit with $400 monthly option .



- **[Starburst](https://www.starburst.io/)**  

  Enterprise platform built on **Trino** (open-source distributed SQL engine). Federates queries across data lakes, warehouses, and databases with enterprise security, cost controls, and **Warp Speed** caching. 50+ connectors. Credit-based pricing: Pro $0.50, Enterprise $0.75, Mission-Critical $1.00 per credit .



- **[CData Virtuality](https://www.cdata.com/)**  

  Data virtualization and integration platform. Provides real-time access to 200+ data sources through a unified SQL interface with advanced query optimization.



- **[TIBCO Data Virtualization](https://www.tibco.com/)**  

  Enterprise data virtualization platform. Provides unified data access, federation, and delivery across disparate sources with metadata management.



- **[IBM Cloud Pak for Data](https://www.ibm.com/)**  

  Data and AI platform with data virtualization capabilities. Provides unified access to data across hybrid cloud environments.



- **[AtScale](https://www.atscale.com/)**  

  Semantic layer platform with virtual OLAP cubes. Provides aggregate awareness rewriting queries against pre-computed rollups. SML (Semantic Modeling Language) open-sourced under Apache in September 2024. Pricing: $10–28 per deployed semantic object per month, floors $2,500–7,000/mo .



- **[Red Hat Data Virtualization](https://www.redhat.com/)**  

  Enterprise data virtualization based on Teiid. Provides unified data access across heterogeneous sources with JBoss-based deployment.



## Open-Source GitHub Projects



### Distributed Query Engines



- **[Trino](https://github.com/trinodb/trino)**  

  **The de facto standard open-source distributed SQL query engine for data virtualization.** **Apache-2.0 licensed** . Federates queries across S3/GCS/ADLS, databases, and warehouses without copying data. Powers **Starburst's commercial platform** . **Key capabilities**: 50+ connectors; ANSI SQL support; interactive query performance on Iceberg/Delta/Hudi; JDBC/ODBC drivers. **Tradeoffs**: Requires DevOps capability for self-management; cold data can be slow; poorly structured lakes become performance traps . **Genuinely viable** for teams with strong engineering.



- **[Teiid](https://github.com/teiid/teiid)**  

  **Open-source data virtualization system for heterogeneous data stores.** **319 stars, 233 forks** . Allows applications to use data from multiple, heterogeneous data stores through a unified SQL interface . **Note**: Repository shows low recent activity (0 commits in last 90 days per OpenSSF scorecard), suggesting project is in maintenance mode . Use with caution for new deployments.



### dbt-Based Virtualization



- **[DVT (Data Virtualization Tool)](https://github.com/dvt-io/dvt-core)**  

  **Cross-engine data transformation built on dbt.** **MIT licensed**, published on PyPI as `dvt-core` . **Core innovation**: Write SQL models that **JOIN tables living on different database engines** — MySQL with Snowflake, Oracle with PostgreSQL, anything with anything — and DVT handles extraction, federation, and loading automatically . **Architecture**: Wrapper around stock dbt-core; dbt runs standard models; DVT picks up models dbt can't express (cross-engine `f_table` and `.py` models) and runs them through its own pipeline: decompose → transpile/pushdown → extract (Sling → Parquet, parallel) → compute (DuckDB joins locally) → load . **Sling direct path**: When all sources share one connection, whole query transpiled and streamed directly — no staging . **Install**: `pip install dvt-core`.



### Semantic Layer



- **[Cube Core](https://github.com/cube-js/cube)**  

  **Open-source headless BI and semantic layer.** **Apache-2.0 (backend) / MIT (clients)** . Engineers author YAML or JavaScript data models; Cube exposes them as **REST, GraphQL, and SQL APIs** with a serious caching and pre-aggregation engine . **Use case**: Sub-second responses at concurrency; embedded analytics; data products. **Pricing**: OSS free; Cube Cloud separate .



- **[OrionBelt Semantic Layer](https://github.com/ralforion/orionbelt-semantic-layer)**  

  **Open-source semantic sidecar compiling YAML models to optimized SQL across 8 engines.** **BSL-1.1 licensed**, v2.7.6, active (May 2026) . **Supported engines**: BigQuery, ClickHouse, Databricks, Dremio, DuckDB, MySQL, PostgreSQL, Snowflake . **Connection surfaces**: REST API (FastAPI/OpenAPI), **Arrow Flight SQL** (JDBC/ODBC/Python), **Postgres wire protocol** (any psql/BI tool) . **2,300+ tests**, full CI, multi-dialect drift snapshots. **MCP server** for AI assistants .



- **[Ontop](https://github.com/ontop/ontop)**  

  **Virtual Knowledge Graph engine for data virtualization.** **Apache-2.0 licensed** . Reformulates SPARQL queries into source queries (KG virtualization) without materializing RDF. **Supported federators**: **Dremio, Denodo, Apache Spark, Trino/Athena** . Enables hybrid KG solutions with virtual and materialized data. Integrates with **GraphDB 9.5** for data virtualization over relational sources .



### Additional Strong Open-Source Options



- **Distributed Query**: **Trino** (de facto standard, powers Starburst), **Teiid** (heterogeneous stores, maintenance mode) .

- **dbt-Based**: **DVT** (cross-engine federation, DuckDB compute, MIT) .

- **Semantic Layer**: **Cube Core** (headless BI, REST/GraphQL/SQL), **OrionBelt** (8 engines, Arrow Flight SQL, Postgres wire) .

- **Knowledge Graph**: **Ontop** (SPARQL-to-SQL, supports Dremio/Denodo/Trino) .

- **Lightweight Federation**: **Duckle** (local-first ETL, DuckDB, complements Dremio/Snowflake) .



**Frameworks for building custom systems**: Combine **Trino** for distributed federated SQL across data lakes and databases, **DVT** for cross-engine dbt transformations with local DuckDB compute, **Cube Core** or **OrionBelt** for semantic layer and metrics APIs, and **Ontop** for virtual knowledge graphs over relational sources. Add **PostgreSQL** for metadata persistence and **Docker** for deployment.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Data virtualization platforms handle sensitive production data; ensure proper access controls, query governance, and compliance with data protection regulations.

- **Open-source reality**: The open-source ecosystem for data virtualization is **mature at the distributed query layer** (**Trino**) and **developing at the semantic layer** (**Cube Core**, **OrionBelt**). **DVT** provides a novel approach to cross-engine federation using dbt and DuckDB . **Teiid** was historically significant but shows low recent activity . However, **commercial platforms** (Denodo, Dremio, Starburst, AtScale) provide **managed infrastructure, advanced query optimization (Reflections, Warp Speed), enterprise governance, and dedicated support** that open-source alternatives require significant operational investment to match. The open-source path is **genuinely viable** for organizations with strong data platform engineering capacity.



---



**Made for data engineers, analytics architects, platform teams, and data platform leads.**

Let's make data virtualization more open, transparent, and federated.
