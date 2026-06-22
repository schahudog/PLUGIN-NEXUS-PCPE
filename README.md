NEXUS·PCPE
Plugin oficial de Inteligência Artificial Investigativa, Pericial e Administrativa da Polícia Civil do Estado de Pernambuco, desenvolvido para o ecossistema Claude + Cowork. Implementa uma arquitetura de 5 agentes especializados e 18 habilidades para produção de peças policiais em conformidade com os padrões institucionais da PCPE e com a Portaria Normativa DG/PCPE Nº 29/2026 — PIGIA.


Versão: 1.2.7
Responsável de adaptação: Agente de Polícia Lukas Furtado — PCPE
Equipe: Del. Gregório Lucas · Del. Dark Blacker · Ag. Lukas Furtado · Esc. Edilson Nascimento
Créditos originais: Prof. Jonas Tomazi / Equipe DataVirtus
Licença: Uso interno — Polícia Civil do Estado de Pernambuco


________________


Visão Geral
O NEXUS·PCPE é um plugin para o Cowork (Claude Desktop) que transforma o Claude em assistente especializado para toda a atividade policial. Não substitui o julgamento profissional — é instrumento de suporte. Toda peça gerada deve ser lida, conferida, adaptada e assinada pelo servidor responsável. A responsabilidade pelo ato é sempre do ser humano.


Requisitos:


* Assinatura Claude compatível com acesso ao Cowork (Claude Max ou superior)
* Aplicativo Claude Desktop com Cowork habilitado


________________


Arquitetura de Agentes
O sistema é orquestrado pelo Delegado, ponto de entrada principal, que analisa cada demanda e decide se resolve diretamente ou aciona um agente especializado.
1. Delegado — Orquestrador Principal
Papel: Chefe da delegacia, estrategista e tomador de decisão.


Habilidades próprias:


* portaria-ip — Portaria de Instauração de IP + ofícios requisitórios
* medidas-cautelares — Representações por medidas cautelares penais
* despacho-saneador — Despachos intermediários e decisões processuais
* relatorio-final — Relatório Final de IP com indiciamento
* diagnostico-ip — Diagnóstico estratégico do inquérito
* ordem-de-servico — Ordem de Serviço para autorizar diligências externas


Quando acionar: envio de material sem comando específico; pedido de "análise completa"; menção a instauração, portaria, cautelar, despacho, relatório ou indiciamento; descrição do estado de um IP com pergunta sobre próximo passo.


________________


2. Escrivão — Especialista em Peças Processuais
Papel: Guardião da fé pública e da formalização processual.


Habilidades:


* oitivas — Termos de declaração, interrogatórios e qualificação
* carta-precatoria — Cartas precatórias para diligências em outra comarca
* analise-contradicoes — Análise forense de contradições entre depoimentos
* auto-prisao-flagrante — Auto de prisão em flagrante e peças conexas


Quando acionar: "preparar oitiva", "termo de declarações", "interrogatório", "carta precatória", "deprecar diligência", "analisar contradições", "auto de flagrante".


________________


3. Investigador — Braço Operacional
Papel: Executor de campo, planejador de diligências e analista de dados.


Habilidades:


* comunicacao-servico — Comunicação de Serviço (estruturada ou narrativa)
* analise-rif — Análise de RIF/COAF com geração de RAF em .docx
* diligencias — Planejamento estratégico de diligências por fase e tipo penal


Quando acionar: "comunicação de serviço", "CS", "compilar dados", "planejar diligências", "analisar RIF", "CSVs do COAF".


________________


4. Perito — Especialista Técnico
Papel: Análise forense financeira e digital, inteligência policial.


Habilidades:


* analise-bancaria — Análise forense de extratos e incompatibilidade patrimonial
* producao-conhecimento — Relatórios de inteligência, mapas de vínculos, fichas de alvo
* analise-digital — Forense digital, metadados, rastros eletrônicos, cadeia de custódia
* laudo-tecnico — Elaboração de laudos periciais estruturados


Quando acionar: "analisar extrato", "incompatibilidade patrimonial", "produzir inteligência", "mapa de vínculos", "metadados", "laudo técnico", "perícia".


________________


5. Revisor — Controle de Qualidade
Papel: Segunda camada de controle independente do autor — equivale a Delegado Assistente ou Assessor Jurídico conferindo antes da assinatura.


⚠️ O Revisor não reescreve o arquivo. Devolve laudo, correções para colar e veredicto.


Habilidade:


* auditoria-peca — Auditoria parágrafo a parágrafo de qualquer peça pronta


Dois modos automáticos:


* Modo A — Auditoria de Fonte: autos anexados → confronta cada afirmação fática contra as fontes primárias.
* Modo B — Auditoria de Consistência: sem autos → verifica coerência interna, citação legal e plausibilidade.


Quando acionar: "revisa essa peça", "audita", "confere antes de assinar", "tem erro nessa peça?", ou ao concluir qualquer documento e aceitar revisão antes da assinatura.


________________


As 18 Habilidades (Skills)
#
	Skill
	Agente
	Documento Gerado
	1
	portaria-ip
	Delegado
	Portaria de Instauração + ofícios
	2
	medidas-cautelares
	Delegado
	Representação por cautelar
	3
	despacho-saneador
	Delegado
	Despacho saneador
	4
	relatorio-final
	Delegado
	Relatório Final de IP (RFIP)
	5
	diagnostico-ip
	Delegado
	Diagnóstico investigativo
	6
	ordem-de-servico
	Delegado
	Ordem de Serviço (OS)
	7
	oitivas
	Escrivão
	Termo de declaração / interrogatório
	8
	carta-precatoria
	Escrivão
	Carta precatória
	9
	analise-contradicoes
	Escrivão
	Análise de contradições
	10
	auto-prisao-flagrante
	Escrivão
	Auto de prisão em flagrante
	11
	comunicacao-servico
	Investigador
	Comunicação de Serviço (CS)
	12
	analise-rif
	Investigador
	Relatório de Análise Financeira (RAF)
	13
	diligencias
	Investigador
	Plano de diligências
	14
	analise-bancaria
	Perito
	Laudo de análise bancária forense
	15
	producao-conhecimento
	Perito
	RI, NIR, ficha de alvo, mapa de vínculos
	16
	analise-digital
	Perito
	Laudo de análise digital
	17
	laudo-tecnico
	Perito
	Laudo técnico pericial
	18
	auditoria-peca
	Revisor
	Laudo de auditoria (chat)
	

________________


Fluxo de Orquestração
╔══════════════════════════════════════════════════════╗


║              USUÁRIO / AUTORIDADE POLICIAL            ║


║          (Envia material ou faz solicitação)          ║


╚═════════════════════╤════════════════════════════════╝


                      │


                      ▼


╔══════════════════════════════════════════════════════╗


║                DELEGADO (Orquestrador)               ║


║  • Analisa contexto e tipo de demanda                ║


║  • Define estratégia (resolve vs. delega)            ║


║  • Autoridade Policial — decisão final               ║


╚═════════════════════╤════════════════════════════════╝


                      │


         ┌────────────┼────────────┐


         ▼            ▼            ▼


   ┌──────────┬──────────────┬──────────┐


   │ ESCRIVÃO │ INVESTIGADOR │  PERITO  │


   │          │              │          │


   │ Oitivas  │ CS / RIF     │ Forense  │


   │ Precatória│ Diligências │ Intelig. │


   │ Contradições│ Levantam. │ Laudos   │


   │ Flagrante│              │          │


   └────┬─────┴──────┬───────┴────┬─────┘


        │            │            │


        └────────────┬────────────┘


                     ▼


   ╔═════════════════════════════════════╗


   ║         REVISOR (Opcional)         ║


   ║  Auditoria antes da assinatura     ║


   ╚═════════════════╤═══════════════════╝


                     │


                     ▼


   ╔═════════════════════════════════════╗


   ║           RESULTADO FINAL           ║


   ║  Peça pronta para revisão e        ║


   ║  assinatura da Autoridade Policial ║


   ╚═════════════════════════════════════╝


________________


Uso Responsável de Dados — Verde / Amarelo / Vermelho
Nível
	Tipo de dado
	Conduta
	🟢 Verde
	Dado público ou administrativo genérico
	Usar normalmente
	🟡 Amarelo
	Dado restrito de processo sem sigilo decretado
	Anonimizar antes de usar
	🔴 Vermelho
	Dado sigiloso sob cadeia de custódia
	Nunca inserir na nuvem — usar IA local
	

Vermelho inclui: RIF completo com identidade real, sigilo bancário e fiscal decretado, interceptação telefônica, inquérito sob segredo de justiça, identidade de colaboradores e vítimas protegidas.


________________


Conformidade com a PIGIA
O NEXUS·PCPE está em conformidade com a Portaria Normativa DG/PCPE Nº 29, de 3 de junho de 2026, que institui a Política Institucional de Governança e Uso Responsável de Sistemas de IA Generativa (PIGIA) e cria a Biblioteca Institucional de Prompts.


Exigência PIGIA
	Como o NEXUS atende
	Natureza auxiliar e não decisória (art. 1º, §§ 2º e 3º)
	Toda peça é preliminar; decisão e assinatura são sempre do servidor
	Hipóteses autorizadas de uso (art. 7º)
	Atua em síntese de textos, minutas, relatórios, revisão e análise preliminar
	Classificação de riscos (arts. 9º e 10)
	Tabela Verde/Amarelo/Vermelho corresponde à classificação baixo/moderado/alto da PIGIA
	Revisão humana qualificada (arts. 14 e 15)
	Agente Revisor operacionaliza a revisão obrigatória antes da assinatura
	Biblioteca Institucional de Prompts (arts. 26 e 27)
	As 18 Skills funcionam como prompts institucionais padronizados
	Vedação ao treinamento com dados institucionais (art. 18, VII)
	A Anthropic garante contratualmente que dados de usuários não treinam modelos públicos
	

A PIGIA entra em vigor em 1º de agosto de 2026.


________________


Cabeçalho Institucional
Todos os documentos gerados adotam o padrão:


POLÍCIA CIVIL DE PERNAMBUCO


DIRETORIA [NOME DA DIRETORIA] — [SIGLA]


[Nº]ª DELEGACIA DE POLÍCIA DE [ESPECIALIDADE] — [SIGLA]


Substitua os arquivos brasao_pcpe.png e brasao_pe_estado.png nas pastas resources\ de cada skill pelos arquivos oficiais da sua unidade após a instalação.


________________


Instalação
1. Abra o Claude Desktop com Cowork habilitado
2. Acesse Settings → Plugins → Install from file
3. Selecione o arquivo nexus-pcpe.plugin
4. Após a instalação, substitua os brasões em cada pasta resources\ das skills


________________


Princípios de Funcionamento
1. Conformidade Institucional — Documentos seguem os padrões da PCPE e da PIGIA
2. Zero Invenção — Nenhum dado é fabricado; toda análise parte do material fornecido
3. Supervisão Humana — A decisão final é sempre da Autoridade Policial
4. Especialização — Cada agente opera exclusivamente em sua área de competência
5. Controle de Qualidade — O Revisor oferece auditoria independente antes da assinatura
6. Segurança de Dados — Classificação Verde/Amarelo/Vermelho em conformidade com a PIGIA
7. Rastreabilidade — Fundamentos legais explícitos em cada peça gerada


________________


Créditos
Função
	Nome
	Delegado de Polícia
	Gregório Lucas
	Delegado de Polícia
	Dark Blacker
	Agente de Polícia (adaptação PCPE)
	Lukas Furtado
	Escrivão de Polícia
	Edilson Nascimento
	Desenvolvimento técnico
	Prof. Jonas Tomazi / DataVirtus
	

________________


Suporte
Para problemas ou sugestões relacionados à adaptação para a PCPE:


* Responsável: Agente de Polícia Lukas Furtado — PCPE


Créditos pela estrutura original:


* Prof. Jonas Tomazi / Equipe DataVirtus — contato@datavirtus.com.br


________________




Última atualização: 22 de junho de 2026
Versão: 1.2.7
