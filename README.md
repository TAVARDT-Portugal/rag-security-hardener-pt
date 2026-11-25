# Hub de Hardening e Blindagem de Segurança em Pipelines RAG

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-5b3cf5.svg)](https://tavardt-portugal.github.io/rag-security-hardener-pt/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

***

Mecanismo de avaliação de segurança e blindagem de contexto para arquiteturas RAG (Retrieval-Augmented Generation) desenvolvido pela **TAVARDT**. Fundamentado nas diretrizes OWASP LLM01, OWASP LLM04, OWASP LLM07 e no framework MITRE ATLAS, o utilitário audita isolamento vetorial multi-tenant, sanitiza injeções indiretas e gera componentes defensivos de middleware.

***

## Capacidades Centrais e Arquitetura Defensiva

* **Auditoria Determinística de Pipelines**: Valida fronteiras contextuais, filtragem de metadados e limites de tokens contra especificações formais de segurança.
* **Geração Automatizada de Middleware**: Exporta classes modulares em Python prontas para higienizar dados de contexto e impor encapsulamento estrito em XML.
* **Verificação de Isolamento Multi-Tenant**: Confirma se consultas vetoriais exigem chaves criptográficas e filtros de metadados para evitar vazamentos de dados entre clientes.

***

## Vetores de Risco e Impacto Operacional

Executar pipelines RAG sem isolamento contextual estruturado permite que instruções maliciosas ocultas em documentos recuperados assumam o controle do modelo e violem dados privados. A ferramenta audita cinco dimensões críticas de segurança:

* **Integridade na Ingestão de Documentos**: Audita esteiras de ingestão contra injeções esteganográficas em PDFs, códigos de controle unicode e formatos maliciosos (Dedução: até -25 pontos).
* **Isolamento Multi-Tenant em Bancos Vetoriais**: Identifica coleções compartilhadas desprovidas de isolamento rigoroso por namespaces ou metadados de controle de acesso (Dedução: até -30 pontos).
* **Encapsulamento de Limites Contextuais**: Bloqueia a concatenação direta de texto ao exigir tags delimitadoras XML com ordens explícitas de não execução (Dedução: até -25 pontos).
* **Filtragem de Injeções Indiretas de Prompt**: Aplica filtros heurísticos de expressões regulares para neutralizar comandos adversariais embutidos nos fragmentos (Dedução: até -20 pontos).
* **Portões de Validação de Saída e Mascaramento**: Impõe verificação de atribuição factual e filtros regex para mascarar dados pessoais antes da resposta ao usuário (Dedução: até -15 pontos).

As esteiras avaliadas recebem uma pontuação acumulada de 10 a 100 pontos. O resultado classifica a arquitetura em **HARDENED** (85 a 100 pontos), **MODERATE** (50 a 84 pontos) ou **CRITICAL** (abaixo de 50 pontos), interrompendo a entrega em ambientes de produção.

***

## Instalação e Execução CLI

Avalie a segurança de pipelines ou exporte componentes de middleware através de comandos Python padronizados:

```bash
# Clonar o repositório oficial
git clone https://github.com/TAVARDT-Portugal/rag-security-hardener-pt.git

# Acessar o diretório de trabalho
cd rag-security-hardener-pt

# Avaliar pipeline RAG em todas as dimensões defensivas
python rag_security_hardener.py -i 3 -v 3 -c 3 -f 3 -g 3

# Exportar middleware de proteção em Python
python rag_security_hardener.py -i 3 -v 3 -c 3 -f 3 -g 3 -e defensive_rag_middleware.py

# Emitir relatório estruturado em formato JSON
python rag_security_hardener.py -i 3 -v 3 -c 3 -f 3 -g 3 -j
```

***

## FAQ Técnico

### Quais vetores de vulnerabilidade o kit de segurança RAG avalia nas esteiras de recuperação?

A ferramenta audita pipelines contra ingestão de documentos não autenticados, vazamento entre tenants em bancos vetoriais, escape de limites contextuais, injeção indireta e saídas desprotegidas. As arquiteturas avaliadas recebem uma pontuação defensiva de 10 a 100 pontos, categorizadas em HARDENED, MODERATE ou CRITICAL.

### Como o encapsulamento de contexto com delimitadores XML previne injeções indiretas de prompt?

O isolamento dos fragmentos recuperados dentro de tags XML estritas estabelece uma fronteira explícita entre dados externos e instruções de sistema. Essa segregação impede que comandos hostis embutidos em documentos de terceiros sejam interpretados como diretrizes executáveis pelo modelo de linguagem.

### Por que a filtragem por metadados de tenant é indispensável em bancos vetoriais multi-tenant?

Sem isolamento rígido por namespaces ou filtragem criptográfica de metadados, buscas semânticas podem recuperar fragmentos pertencentes a diferentes clientes. A aplicação de controles de acesso no momento da consulta anula o risco de vazamentos laterais de informações confidenciais entre organizações.

### Quais recursos defensivos são disponibilizados pelo blueprint de middleware exportado?

A geração do blueprint com o parâmetro -e exporta uma classe defensiva em Python pronta para filtrar padrões maliciosos e normalizar delimitadores antes da montagem do prompt. Essa camada de sanitização intercepta tentativas de anulação de instruções e requisições de extração de credenciais em tempo de execução.

### O kit de hardening pode ser integrado para validação contínua em esteiras de CI/CD?

Os utilitários CLI processam parâmetros de arquitetura ou arquivos de configuração emitindo relatórios estruturados através da opção -j. Esteiras de integração contínua podem analisar programaticamente o escore JSON para bloquear a promoção de pipelines que violem os padrões de segurança.

***

## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/pt/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/pt/
* **Contacto Técnico:** https://ag.tavardt.com/pt/contacto/

***

### Licença
Distribuído sob a Licença MIT. Consulte [LICENSE](LICENSE) para obter detalhes completos.

***

© 2026 TAVARDT. Todos os direitos reservados.
