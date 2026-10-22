# Núcleo do ICM

Fonte adaptada: [RinDig/icm-architect](https://github.com/RinDig/icm-architect), commit `8f9cdf95e5051f126babc455b7a0558426db43d4` (MIT, 2026 Jake Van Clief).

## Hierarquia de contexto

| Camada | Arquivo típico | Pergunta | Regra |
|---|---|---|---|
| L0 | `AGENTS.md` | Onde estou? | Roteia; não carrega conteúdo. |
| L1 | `CONTEXT.md` raiz | Para onde vou? | Mapa da estrutura. |
| L2 | `CONTEXT.md` da etapa | O que faço? | Ponto de controle: entradas explícitas. |
| L3 | `references/`, `_shared/` | Quais regras valem? | Fábrica estável. |
| L4 | `output/`, insumos da execução | Em que trabalho? | Produto por execução. |

L0–L2 são catálogo. L3 é a receita. L4 são os insumos e resultados. Uma etapa deve carregar apenas o necessário, em geral entre 2 mil e 8 mil tokens.

## Formato do contrato de etapa

```markdown
# 02_script — transformar pesquisa em roteiro
Uma função: escrever roteiro a partir da pesquisa.

## Entradas
- Trabalho: ../01_pesquisa/output/pesquisa.md
- Referência: ../../_shared/voz.md
- Referência: references/estrutura.md

## Processo
1. Leia a pesquisa.
2. Escreva seguindo a estrutura e a voz declaradas.
3. Respeite as restrições da etapa.

## Saídas
- output/rascunho.md

## Checagem humana
Leia o texto em voz alta e edite o arquivo; a próxima etapa lê a versão deixada aqui.
```

Entradas são caminhos exatos e separam trabalho de referência. O processo é curto; detalhes estáveis pertencem a L3. Há uma checagem humana concreta, não “revisar”.

## Convenções

- Etapas: `NN_nome-em-kebab` (`01_pesquisa`).
- Pastas de sistema: `_meta/`, `_shared/`, `_templates/`, `_index/`, `_archive/`.
- Registros: escolha kebab-case ou títulos humanos e registre a escolha no esquema.
- Arquivo de entrada: `AGENTS.md`; se um host usar outra convenção, gere um apontador — não mantenha cópias manuais.
- Índices gerados nunca são editados manualmente.

## Onde ICM perde

Não use como substituto de infraestrutura quando houver colaboração multiagente em ciclos rápidos, alta concorrência ou ramificação automática complexa. Para trabalho sequencial, repetível e revisado por humanos, a estrutura vence código de orquestração desnecessário.