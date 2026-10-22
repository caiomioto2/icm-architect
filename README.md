# ICM Architect — português brasileiro

Adaptação em português brasileiro da habilidade **ICM Architect**, baseada no método **Interpretable Context Methodology (ICM)** de Jake Van Clief.

A estrutura de arquivos conduz o trabalho: diretórios numerados exprimem sequência, a hierarquia delimita contexto, Markdown guarda estado e cada resultado intermediário continua editável por pessoas.

## Conteúdo

- `SKILL.md`: instruções principais, modos de construção e reestruturação e teste de caminhada.
- `references/`: fundamentos do método e formas de workspace.
- `templates/`: modelos copiáveis para arquivos de entrada, contratos, nós, esquema e questionário.

## Uso

Copie a pasta `icm-architect` para o diretório de habilidades do agente e siga as instruções em `SKILL.md`. A habilidade exige capacidade de ler, listar, escrever, mover e verificar arquivos; sem escrita, ela deve entregar a árvore-alvo e o mapa de migração sem afirmar que alterou o workspace.

## Proveniência e licença

Adaptação agnóstica de agente do repositório [RinDig/icm-architect](https://github.com/RinDig/icm-architect), commit `8f9cdf95e5051f126babc455b7a0558426db43d4`, por Jake Van Clief. A adaptação remove acoplamento a Claude e usa `AGENTS.md` como convenção padrão neutra. Distribuída sob a licença MIT; veja `LICENSE`.
