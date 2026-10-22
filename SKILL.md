---
name: icm-architect
version: 1.0.0
license: MIT
upstream:
  repository: https://github.com/RinDig/icm-architect
  commit: 8f9cdf95e5051f126babc455b7a0558426db43d4
  author: Jake Van Clief
  adapted_for: agent-agnostic
description: Use to build or restructure an ICM workspace for any agent.
tags:
  - workspace-architecture
  - knowledge-management
  - process-design
  - agent-agnostic
triggers:
  - "ICM isso"
  - "estruture isso para agentes"
  - "crie um workspace"
  - "organize esse repositório"
  - "reorganize essa pasta"
  - "organize esse vault"
  - "arquitetura de pastas para agentes"
  - "pipeline de arquivos"
---

# ICM Architect

Adaptação agnóstica de agente do método **Interpretable Context Methodology (ICM)**, por Jake Van Clief. A estrutura de arquivos conduz o trabalho: diretórios numerados exprimem sequência, a hierarquia delimita contexto, Markdown guarda estado e cada resultado intermediário é editável por humanos.

A habilidade exige um agente capaz de ler, listar, escrever, mover e verificar arquivos. Se não houver escrita, produza a árvore-alvo e o mapa de migração; não finja que a estrutura foi criada.

## Contrato

Uma execução está concluída quando o workspace passa no **teste de caminhada**: um agente sem memória consegue se orientar, executar uma etapa e informar o estado lendo o arquivo de entrada e, no máximo, dois arquivos adicionais.

Aplique a escada certa: conversa → prompt salvo/habilidade → workspace ICM. Não construa arquitetura para um processo que ainda não se repetiu. Se cabe em um prompt salvo, pare ali.

## Princípios invariáveis

1. **Uma pasta, uma função.** Cada diretório executa uma etapa ou concentra um tipo de registro.
2. **Arquivo de entrada pequeno.** Use `AGENTS.md` como padrão neutro — Claude Code o suporta nativamente. Se algum host realmente exigir outro nome, crie um apontador gerado para `AGENTS.md`; nunca duas versões mantidas manualmente.
3. **Numeração carrega sequência.** Use `01_nome-da-etapa`, `02_nome-da-etapa` onde ordem importa.
4. **Contrato explícito por etapa.** Cada diretório de trabalho possui `CONTEXT.md` com entradas, processo, saídas e uma checagem humana.
5. **Fábrica separada de produto.** Regras e modelos estáveis ficam em `_shared/`, `references/` ou `_templates/`; resultados de cada execução ficam em `output/`.
6. **Cada saída é editável.** Nada avança sem uma superfície que uma pessoa possa abrir e corrigir.
7. **Carregamento seletivo.** A etapa lê apenas o arquivo de entrada, seu contrato, referências necessárias e insumos declarados.
8. **Texto simples e uma casa por fato.** Markdown + frontmatter; link vence cópia.
9. **Filesystem como estado.** O estado é derivável dos artefatos existentes; índices gerados não são editados à mão.
10. **Instanciar copiando.** Novo trabalho nasce de um modelo, não de página vazia.

## Modo 1 — Construir

1. Extraia a unidade que se repete, as etapas reais, as pausas de julgamento humano, o que é estável e o artefato final.
2. Escolha a forma: **pipeline**, **guarda-chuva**, **biblioteca de registros**, **pacote de conhecimento** ou **mapa de contexto**. Carregue `references/forms.md` antes dessa escolha.
3. Crie a menor árvore que sustenta o processo. Três etapas comprovadas vencem sete imaginadas.
4. Escreva `AGENTS.md`, o `CONTEXT.md` de raiz e um contrato por etapa. Use os modelos em `templates/`.
5. Rode o teste de caminhada e corrija a estrutura, não a explicação.

## Modo 2 — Reestruturar

1. Faça inventário sem mover nem apagar nada.
2. Identifique a forma que já existe sob a bagunça: pipeline, biblioteca ou mapa.
3. Classifique cada arquivo: **catálogo**, **contrato**, **fábrica**, **produto** ou **legado**.
4. Apresente árvore-alvo e mapa `origem → destino → função`; aguarde aprovação antes de mover.
5. Migre, remova duplicação por links e arquive legados — nunca apague silenciosamente.
6. Rode o teste de caminhada.

## Teste de caminhada

- A raiz explica onde o agente está e para onde ir pela tarefa atual?
- A etapa nomeia caminhos exatos de entrada, processo, saída e checagem humana?
- O estado é legível ao inspecionar `output/` ou frontmatter?
- Arquivos de roteamento apontam para conteúdo em vez de carregar conteúdo?
- Cada fato possui uma única casa?
- Entrada + contrato + referências + insumos ficam, em regra, entre 2 mil e 8 mil tokens?

## Referências e modelos

- `references/core.md` — hierarquia de contexto, contratos, nomes, disciplina de tokens e limites do método.
- `references/forms.md` — formas, árvores iniciais, movimentos e falhas recorrentes.
- `templates/AGENTS.md` — arquivo de entrada neutro.
- `templates/CONTEXT.md`, `templates/stage-CONTEXT.md`, `templates/node.md`, `templates/schema.md`, `templates/questionnaire.md` — modelos copiáveis.

## Modos de capacidade

- **Completo:** lê, cria/move arquivos e verifica a árvore final.
- **Rascunho:** pode entregar árvore, contratos e mapa de migração, mas não altera arquivos.
- **Bloqueado:** não consegue ler a pasta ou repositório-alvo; peça o caminho ou os arquivos mínimos.

## Anti-padrões

- Criar um workspace antes de executar o processo manualmente o suficiente para descobrir suas etapas reais.
- Usar ICM para colaboração multiagente em tempo real, alta concorrência ou ramificação automatizada complexa.
- Criar dois arquivos de entrada que divergem.
- Transformar arquivo de roteamento em depósito de contexto.
- Misturar regras estáveis com artefatos de uma execução.
- Criar pastas vazias, `misc` ou profundidade especulativa.
- Mover, excluir ou renomear durante o inventário sem aprovação explícita.
- Tentar contornar o guardião quando `AGENTS.md` for tratado como arquivo protegido. Obtenha aprovação explícita imediatamente antes da escrita; se o prompt expirar, pare, peça nova confirmação e só repita após uma nova mensagem do usuário.

## Proveniência

Método adaptado de [RinDig/icm-architect](https://github.com/RinDig/icm-architect), commit `8f9cdf95e5051f126babc455b7a0558426db43d4`, licenciado sob MIT (copyright 2026 Jake Van Clief). A adaptação remove acoplamento a Claude e usa `AGENTS.md` como convenção padrão neutra.