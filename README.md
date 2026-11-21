# Validador e Blindador de Segurança para Pipelines RAG - TAVARDT Portugal

> Auditoria de Isolamento de Contexto, Prevenção de Injeção Indireta e Blindagem Defensiva de IA

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Active-brightgreen)](https://tavardt-portugal.github.io/rag-security-hardener-pt/)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Security: OWASP LLM](https://img.shields.io/badge/Security-OWASP%20LLM01%20%7C%20LLM02-red.svg)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

## Visão Geral da Arquitetura e Segurança RAG

O ecossistema de Recuperação Aumentada por Geração (RAG - Retrieval-Augmented Generation) introduz vetores críticos de vulnerabilidade em aplicações corporativas de inteligência artificial. Ao ingerir documentos externos, websites e bases de conhecimento para alimentar o contexto de modelos de linguagem (LLMs), a aplicação fica exposta a ataques de Injeção Indireta de Prompt (OWASP LLM01) e Vazamento de Dados Multi-inquilino (OWASP LLM02).

Este repositório fornece tanto uma aplicação web interativa executada 100% no navegador quanto um utilitário CLI em Python de biblioteca padrão para auditar arquiteturas RAG e gerar blueprints de blindagem defensiva.

## Aplicação Web Interativa

Acesse a ferramenta online e audite seu pipeline em tempo real:

- [https://tavardt-portugal.github.io/rag-security-hardener-pt/](https://tavardt-portugal.github.io/rag-security-hardener-pt/)

## Utilização do Scanner CLI (Python)

O utilitário `rag_security_hardener.py` opera exclusivamente com a biblioteca padrão do Python (sem dependências externas) e permite automatizar a auditoria em pipelines de CI/CD ou ambientes de desenvolvimento local.

```bash
# Executar avaliacao interativa com parametros padrao
python rag_security_hardener.py

# Exportar middleware defensivo para uso imediato em seu pipeline
python rag_security_hardener.py --export-blueprint secure_rag_middleware.py

# Executar auditoria em modo JSON para integracao em CI/CD
python rag_security_hardener.py --ingestion 3 --vector-db 3 --context-boundary 3 --indirect-filter 3 --json
```

## Controles Arquiteturais e Mitigações Defensivas

1. **Isolamento de Contexto**: Encapsulamento estrito de blocos de contexto recuperados utilizando delimitadores XML (`<untrusted_context>`) e instruções de sistema impermeáveis.
2. **Prevenção de Injeção Indireta**: Sanitização heurística de instruções embutidas e anomalias semânticas em documentos ingeridos.
3. **Isolamento Multi-inquilino (Multi-Tenant RBAC)**: Segregação estrita de vetores por namespaces e validação criptográfica de permissões em tempo de busca.
4. **Gate de Saída e Fiscalização de Citações**: Verificação de atribuição de respostas para erradicar alucinações e mascaramento ativo de dados sensíveis.

## Portais Oficiais

- **Portal Oficial TAVARDT**: [https://ag.tavardt.com/pt/](https://ag.tavardt.com/pt/)
- **Central de Ferramentas**: [https://tools.tavardt.com/pt/](https://tools.tavardt.com/pt/)
- **Contacto**: [https://ag.tavardt.com/pt/contact/](https://ag.tavardt.com/pt/contact/)

---
&copy; 2026 TAVARDT Portugal. Todos os direitos reservados.
