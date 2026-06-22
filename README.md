# NEXUS·PCPE

Plugin para uso institucional de investigação policial da **Polícia Civil do Estado de Pernambuco**, com arquitetura de agentes especializados para produção de peças policiais em conformidade com os padrões institucionais da PCPE.

**Versão:** 1.5.1
**Autor:** Lukas Furtado — PCPE

**Créditos originais:** Equipe DataVirtus, Prof. Jonas Tomaz

**Licença:** Uso interno — Polícia Civil do Estado de Pernambuco

**Colaboradores:**

Delegado de Polícia Gregório Lucas

Delegado de Polícia Dark Blacker

Agente de Polícia Lukas Furtado

Escrivão de Polícia Edilson Nascimento

Desenvolvimento técnico · Prof. Jonas Tomazi / DataVirtus

---

## Visão Geral

O **NEXUS** é um plugin para o Cowork (Claude Desktop) que transforma o Claude em assistente especializado para toda a atividade policial. Não substitui o julgamento profissional — é instrumento de suporte. Toda peça gerada deve ser lida, conferida, adaptada e assinada pelo servidor responsável. A responsabilidade pelo ato é sempre do ser humano.

Requisitos:
Assinatura Claude compatível com acesso ao Cowork (Claude Max ou superior)
Aplicativo Claude Desktop com Cowork habilitado

**Arquitetura de Agentes:**
O sistema é orquestrado pelo Delegado, ponto de entrada principal, que analisa cada demanda e decide se resolve diretamente ou aciona um agente especializado.

- **Delegado** — Chefe da delegacia, ponto de entrada, estrategista e tomador de decisão
- **Escrivão** — Guardião da fé pública, especialista em peças cartorárias e processuais
- **Investigador** — Braço operacional, planejador de diligências e analista de dados
- **Perito** — Especialista técnico em análise forense, financeira e digital
- **Revisor (Auditor)** — Segunda camada de controle de qualidade: audita peças prontas parágrafo a parágrafo, sem alterar o arquivo final

O sistema é orquestrado pelo **Delegado**, que recebe toda demanda, analisa o contexto e decide se:
1. Resolve a demanda diretamente com suas próprias habilidades, ou
2. Aciona um (ou mais) agentes especializados para executar tarefas específicas

Todos os documentos gerados seguem o padrão institucional da PCPE, com cabeçalho oficial em 3 linhas centralizado, brasão da PCPE à esquerda e brasão do Estado de Pernambuco à direita.

---

## Cabeçalho Institucional

Todos os documentos gerados pelo plugin adotam o seguinte padrão de cabeçalho:

```
POLÍCIA CIVIL DE PERNAMBUCO
DIRETORIA [NOME DA DIRETORIA] — [SIGLA]
[Nº]ª DELEGACIA DE POLÍCIA DE [ESPECIALIDADE] — [SIGLA]
```

Os brasões são configuráveis por unidade. Após a instalação, substitua os arquivos `brasao_pcpe.png` e `brasao_pe_estado.png` nas pastas `resources\` de cada skill pelos arquivos oficiais da sua unidade.

---

## Arquitetura de Agentes

### 1. Delegado (Orquestrador Principal)

**Papel:** Chefe da delegacia e maestro da investigação

**Habilidades Diretas (Resolve Sozinho):**
- `portaria-ip` — Instauração de Inquérito Policial + ofícios requisitórios
- `medidas-cautelares` — Representações por medidas cautelares penais
- `despacho-saneador` — Despachos intermediários e decisões processuais
- `relatorio-final` — Relatório final com indiciamento e conclusões
- `diagnostico-ip` — Diagnóstico estratégico e mapeamento processual

**Delegação (Aciona Outros Agentes):**
- Aciona **Escrivão** para oitivas, cartas precatórias, análise de contradições
- Aciona **Investigador** para levantamento de dados, análise RIF, planejamento de diligências
- Aciona **Perito** para análise bancária, produção de inteligência, análise digital

**Quando Acioná-lo:**
- Usuário envia material sem especificar comando concreto
- Usuário pede "análise completa" ou "pacote completo"
- Usuário menciona: instauração, portaria, cautelar, despacho, relatório, indiciamento
- Usuário descreve o estado de um IP e pergunta o que fazer
- Usuário envia múltiplos arquivos de naturezas diferentes

---

### 2. Escrivão (Especialista em Peças Processuais)

**Papel:** Guardião da fé pública e formalização processual

**Habilidades Diretas:**
- `oitivas` — Preparação de termos de declaração e interrogatórios
- `carta-precatoria` — Elaboração de cartas precatórias e pedidos de cooperação
- `analise-contradicoes` — Análise forense de contradições entre depoimentos
- `auto-prisao-flagrante` — Lavro de auto de prisão em flagrante delito

**Quando Acioná-lo:**
- "Preparar oitiva", "termo de declarações", "interrogatório"
- "Carta precatória", "deprecar diligência"
- "Analisar contradições", "confrontar depoimentos"
- "Auto de flagrante", "lavrar flagrante"

---

### 3. Investigador (Braço Operacional)

**Papel:** Executor de operações, planejador de diligências, analista de dados

**Habilidades Diretas:**
- `comunicacao-servico` — Compilação de Comunicação de Serviço (CS estruturada ou narrativa)
- `analise-rif` — Análise de Relatórios de Inteligência Financeira do COAF
- `diligencias` — Planejamento estratégico de diligências por fase e tipo penal

**Quando Acioná-lo:**
- "Comunicação de Serviço", "CS", "compilar dados"
- "Planejar diligências", "quais diligências", "o que fazer"
- "Analisar RIF", "CSVs do COAF", "dados do COAF"
- "Levantamento", "pesquisa de investigado"

---

### 4. Perito (Especialista Técnico)

**Papel:** Análise forense, especialização técnica, inteligência policial

**Habilidades Diretas:**
- `analise-bancaria` — Análise forense de extratos, movimentação, compatibilidade patrimonial
- `producao-conhecimento` — Relatórios de inteligência, mapas de vínculos, fichas de alvo
- `analise-digital` — Forense digital, metadados, rastros eletrônicos
- `laudo-tecnico` — Elaboração de laudos periciais

**Quando Acioná-lo:**
- "Analisar extrato", "movimentação bancária", "incompatibilidade patrimonial"
- "Produzir inteligência", "mapa de vínculos", "ficha do alvo"
- "Metadados", "rastros digitais", "laudo técnico", "perícia"

---

### 5. Revisor / Auditor (Controle de Qualidade)

**Papel:** Segunda camada de controle de qualidade, independente do autor da peça — equivale a um Delegado Assistente ou Assessor Jurídico que confere o trabalho antes da assinatura

**Ferramentas:** somente leitura — **não reescreve o arquivo final**

**Habilidade Direta:**
- `auditoria-peca` — Auditoria parágrafo a parágrafo de qualquer peça pronta (RFIP, RAF, CS, portaria, despacho, cautelar, oitiva, laudo, precatória, flagrante, produto de inteligência)

**Dois modos automáticos:**
- **Modo A — Auditoria de Fonte:** há autos/fontes anexados → confronta cada afirmação fática contra as fontes primárias, com citação e página.
- **Modo B — Auditoria de Consistência:** peça criada sem fontes → verifica coerência interna, citação legal, plausibilidade de datas/prazos/prescrição.

**Quando Acioná-lo:**
- "Revisa", "audita", "confere", "valida essa peça", "tem erro nessa peça?", "está pronta para assinar?"
- Ao concluir qualquer peça, os demais agentes oferecem submetê-la ao Revisor (o usuário decide).

**Saída:** laudo parágrafo a parágrafo (✅/⚠️/⚪), gravidade (BAIXA/MÉDIA/ALTA), resumo quantitativo, bloco de correções para colar, veredicto e recomendação operacional.

---

## Fluxo de Orquestração

```
╔═════════════════════════════════════════════════════════════╗
║                        USUÁRIO / AUTORIDADE                 ║
║              (Envia material ou faz solicitação)             ║
╚════════════════════════════╤════════════════════════════════╝
                             │
                             ▼
╔═════════════════════════════════════════════════════════════╗
║                     DELEGADO (Orquestrador)                 ║
║  • Analisa contexto e tipo de demanda                       ║
║  • Define estratégia (resolve vs. delega)                   ║
║  • Toma decisão final (Autoridade Policial)                 ║
╚════════════════════════════╤════════════════════════════════╝
                             │
            ┌────────────────┼────────────────┐
            │                │                │
            ▼                ▼                ▼
      ┌──────────────┬──────────────┬──────────────┐
      │  ESCRIVÃO    │ INVESTIGADOR │    PERITO    │
      │ (Cartório)   │  (Campo)     │  (Técnico)   │
      │              │              │              │
      │ • Oitivas    │ • CS         │ • Análise    │
      │ • Precatória │ • RIF/COAF   │   Bancária   │
      │ • Contradição│ • Diligências│ • Inteligência│
      │ • Flagrante  │ • Levantamen.│ • Laudo      │
      └────┬─────────┴────┬─────────┴──────┬───────┘
           │              │                │
           └──────────────┬────────────────┘
                          │
                          ▼
      ╔═════════════════════════════════════╗
      ║   Retorno ao DELEGADO para         ║
      ║   • Síntese de resultados          ║
      ║   • Decisão final                  ║
      ║   • Documento consolidado          ║
      ╚═════════════════╤═══════════════════╝
                        │
                        ▼
      ╔═════════════════════════════════════╗
      ║         RESULTADO FINAL             ║
      ║  (Relatório, Portaria, Despacho)   ║
      ╚═════════════════════════════════════╝
```

---

## Documentos Gerados - 19+ habilidades disponíveis no Plugin NEXUS·PCPE

| Documento | Agente Responsável | Formato |
|-----------|-------------------|---------|
| Portaria de Instauração de IP | Delegado | .docx |
| Representação por Medida Cautelar | Delegado | .docx |
| Despacho Saneador | Delegado | .docx |
| Relatório Final de IP (RFIP) | Delegado | .docx |
| Relatório de Análise Financeira (RAF) | Investigador | .docx |
| Comunicação de Serviço (CS) | Investigador | .docx |
| Plano de Diligências | Investigador | .docx |
| Termo de Declaração / Oitiva | Escrivão | .docx |
| Carta Precatória | Escrivão | .docx |
| Análise de Contradições | Escrivão | .docx |
| Auto de Prisão em Flagrante | Escrivão | .docx |
| Análise Bancária Forense | Perito | .docx |
| Relatório de Inteligência (RI/NIR) | Perito | .docx |
| Ficha de Alvo / Mapa de Vínculos | Perito | .docx |
| Laudo Técnico | Perito | .docx |
| Laudo de Auditoria de Peça | Revisor | Chat (laudo + correções para colar) |
| Ordem de serviço | Delegado | .docx |
| Nexus Skill Creator | Especial | .skill |
---

## Fluxo de Análise Completa ("Analisa Tudo")

Quando o usuário envia múltiplos arquivos ou solicita análise completa, o Delegado executa um pipeline em 6 fases:

**Fase 0 — Inventário:** catalogação de todo material recebido (autos, ofícios, extratos, RIF, etc.)

**Fase 1 — Diagnóstico (Delegado):** análise estratégica do IP, gaps probatórios, próximas ações

**Fase 2 — Análise Financeira:** Investigador processa RIF/COAF; Perito analisa extratos bancários

**Fase 3 — Análise de Caso:** Escrivão mapeia contradições, depoimentos e qualificações

**Fase 4 — Planejamento de Diligências:** Investigador define estratégia baseada nos gaps identificados

**Fase 5 — Produtos de Inteligência:** Perito gera relatórios, mapas de vínculos e fichas de alvo

**Fase 6 — Síntese (Delegado):** consolidação, decisão e emissão de portaria/cautelar/despacho ou relatório final

---

## Princípios de Funcionamento

1. **Conformidade Institucional** — Todos os documentos seguem os padrões da PCPE
2. **Zero Alucinação** — Nenhum dado é inventado; toda análise é baseada no material fornecido
3. **Prazos e Prescrição** — Cálculos de prazos processuais incluídos quando pertinentes
4. **Autoridade Policial** — A decisão final é sempre da Autoridade Policial (usuário), nunca do agente
5. **Especialização** — Cada agente opera exclusivamente em sua área de competência
6. **Controle de Qualidade** — O Revisor oferece auditoria independente antes da assinatura
7. **Confidencialidade** — Dados sensíveis tratados em conformidade com a LGPD

---

## Instalação

1. Abra o **Cowork** (Claude Desktop)
2. Acesse **Settings → Plugins → Install from file**
3. Selecione o arquivo `delegacia-pcpe.plugin`
4. Após a instalação, na tela principal do Cowork, abra uma "nova tarefa", indique o que deseja fazer, forneça as informações necessárias e aperfeiçoe o seu trabalho. O NEXUS guia o processo — Antes revise, durante valide e, ao final, assine.

---

## Suporte

Para problemas ou sugestões relacionados à adaptação para a PCPE:
- Responsável: Lukas Furtado — PCPE

Créditos pela estrutura original do plugin:
- Equipe DataVirtus — contato@datavirtus.com.br
- Prof. Jonas Tomaz

