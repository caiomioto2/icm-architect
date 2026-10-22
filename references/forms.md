# As cinco formas do ICM

Fonte adaptada: [RinDig/icm-architect](https://github.com/RinDig/icm-architect), commit `8f9cdf95e5051f126babc455b7a0558426db43d4` (MIT, 2026 Jake Van Clief).

Pergunta de seleção: **qual é a unidade que se repete?**

| Unidade | Forma |
|---|---|
| Uma execução com as mesmas etapas e nova entrega | Pipeline |
| Várias execuções que compartilham identidade e referências | Guarda-chuva |
| Um registro que acumula com o tempo | Biblioteca de registros |
| O produto é o próprio conhecimento navegável | Pacote de conhecimento |
| O assunto é uma organização, seus fluxos e conexões | Mapa de contexto |

## Pipeline

```text
workspace/
├─ AGENTS.md
├─ CONTEXT.md
├─ stages/
│  ├─ 01_pesquisa/{CONTEXT.md,references/,output/}
│  ├─ 02_roteiro/{CONTEXT.md,references/,output/}
│  └─ 03_producao/{CONTEXT.md,references/,output/}
├─ _shared/
└─ setup/questionnaire.md
```

Cada saída de uma etapa é a entrada da próxima e passa por uma pausa humana. Separe etapas que fazem duas coisas. Não construa pipeline para processo não comprovado.

## Guarda-chuva

Uma raiz de roteamento conecta pipelines independentes que compartilham referências estáveis — por exemplo, voz, posicionamento e design. A raiz mapeia tarefas para pipelines; ela não descreve o interior deles.

## Biblioteca de registros

```text
workspace/
├─ AGENTS.md
├─ _index/log.md
├─ _templates/registro/
├─ 01_referencias/
└─ records/<slug>/
```

Cada registro nasce de cópia de modelo. O índice guarda uma linha por registro, identificador e estado. Não deixe o índice virar depósito de conteúdo.

## Pacote de conhecimento

Use quando a entrega é um modelo navegável de um domínio. Separe corpus bruto, pipeline de extração e produto. Cada nota deve ter frontmatter tipado, links e nível de acesso quando houver material sensível. Carregue por camada; nunca engula o pacote inteiro.

## Mapa de contexto

Use para mapear uma organização. Defina um conjunto pequeno de tipos de nó em `_meta/schema.md` — equipe, processo, trabalho, ativo de dados, governança e padrão. Os nós declaram entradas, movimento, saídas e conexões. Um padrão só vira padrão após três ocorrências independentes.

## Composição

Formas podem aninhar: pipeline que gera registros, biblioteca cujos registros são pacotes de conhecimento, ou guarda-chuva de pipelines. A regra não muda: cada nível tem catálogo pequeno que aponta para o nível abaixo e para ali.