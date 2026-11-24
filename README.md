# Hub de Hardening e Blindagem de Segurança em Pipelines RAG

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-5b3cf5.svg)](https://tavardt-portugal.github.io/rag-security-hardener-pt/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![OWASP LLM](https://img.shields.io/badge/OWASP-LLM%20Top%2010-red.svg)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
[![MITRE ATLAS](https://img.shields.io/badge/MITRE-ATLAS%20Matrix-orange.svg)](https://atlas.mitre.org/)

**Hub de Arquitetura Defensiva e Blueprints de Hardening para Pipelines RAG (Retrieval-Augmented Generation)**

Desenvolvido e mantido pela divisão de engenharia de segurança em inteligência artificial da **TAVARDT Portugal**.

***

## Portais Oficiais

* **Portal Institucional**: [Portal Institucional](https://ag.tavardt.com/pt/)
* **Central de Ferramentas**: [Central de Ferramentas](https://tools.tavardt.com/pt/)
* **Canal de Atendimento e Suporte Técnico**: [https://ag.tavardt.com/pt/contacto/](https://ag.tavardt.com/pt/contacto/)

***

## Demonstração Online e Hub de Arquitetura Defensiva

Você pode acessar a especificação técnica corporativa, os testes de diagnóstico arquitetural e os blueprints de mitigação diretamente pelo navegador:

* **[Aplicação Web Oficial no GitHub Pages](https://tavardt-portugal.github.io/rag-security-hardener-pt/)**
* **Central de Ferramentas TAVARDT**

> [!NOTE]
> **Escopo de Execução Técnica:** Este hub web fornece especificações de arquitetura defensiva e blueprints de configuração. Auditorias ativas de bancos vetoriais e integridade de contexto exigem credenciais de ambiente e execução na esteira da aplicação via o utilitário CLI oficial disponibilizado neste repositório (`rag_security_auditor.py`). Páginas web em sandbox de navegador não possuem permissão para conectar diretamente a bancos vetoriais privados.

***

## Blueprints Técnicos de Hardening

1. **rag-security-policy.yml:** Políticas corporativas de segurança definindo limites de chunks, tags XML de isolamento de contexto e regras de validação semântica.
2. **rag_chunk_sanitizer.py:** Pipeline de sanitização para remoção de caracteres invisíveis Unicode, sequências de escape e marcadores de injeção de prompt antes da geração de embeddings.
3. **vector_acl_filter.json:** Esquema de consulta vetorial impondo filtros obrigatórios de controle de acesso (RBAC/ACL) por usuário e tenant para impedir exfiltração entre organizações.
4. **rag_context_template.xml:** Template de envelopamento de contexto delimitado por tags XML com diretrizes estritas de não execução para modelos LLM.
5. **rag_security_auditor.py:** Utilitário CLI local determinístico executado no ambiente da aplicação para auditar diretamente configurações de pipelines RAG e conformidade com OWASP LLM.

***

## Uso do Utilitário CLI Determinístico

Para executar a inspeção determinística diretamente no ambiente do pipeline RAG:

```bash
# 1. Baixar o script de auditoria do repositório oficial
curl -sO https://raw.githubusercontent.com/TAVARDT-Portugal/rag-security-hardener-pt/main/rag_security_auditor.py

# 2. Inspecionar pipeline e especificações defensivas
python3 rag_security_auditor.py

# 3. Exportar diagnóstico em formato estruturado JSON
python3 rag_security_auditor.py -json
```

***

© 2026 TAVARDT. Todos os direitos reservados.
