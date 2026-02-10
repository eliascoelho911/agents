# Agent Configurations

Backup de configurações de agentes de IA (OpenCode, Claude Code, etc.) - globais e por tipo de projeto.

## Estrutura

```
agents/
├── skills/              # Skills publicáveis no skills.sh
│   ├── fast-spec/
│   ├── git-commit/
│   └── pr-creator/
├── opencode/            # Configurações globais do OpenCode
│   └── opencode.json
├── project/             # Configurações por tipo de projeto
│   └── python/
│       └── opencode.json
└── speckit-ptbr/        # Templates do Spec Kit em português
    └── .specify/
        └── templates/
```

## Instalação de Skills

As skills estão publicadas no [skills.sh](https://skills.sh) e podem ser instaladas via CLI:

### Fast Spec

```bash
npx skills add https://github.com/eliascoelho911/agents --skill fast-spec
```

Executa o pipeline completo de especificação (specify → clarify → plan → tasks → analyze) orquestrando comandos speckit com isolamento de contexto.

### Git Commit

```bash
npx skills add https://github.com/eliascoelho911/agents --skill git-commit
```

Executa git commit com análise de mensagem conventional commit, staging inteligente e geração de mensagem. Suporta detecção automática de tipo e escopo, staging inteligente e geração de mensagens seguindo a especificação Conventional Commits.

### PR Creator

```bash
npx skills add https://github.com/eliascoelho911/agents --skill pr-creator
```

Cria Pull Requests de alta qualidade seguindo templates e padrões do repositório. Inclui verificação de branch, preflight checks, busca de templates e criação via GitHub CLI.

## Configurações por Projeto

Copie a configuração apropriada para seu projeto:

### Python

```bash
cp project/python/opencode.json /caminho/do/seu/projeto/
```

**O que inclui:**
- `opencode.json`: Configurações específicas para projetos Python
  - Permissões estendidas para ferramentas Python
  - Formatter ruff
  - LSP basedpyright
  - Keybinds personalizados

## Spec Kit em Português (speckit-ptbr)

Templates traduzidos do [Spec Kit](https://github.com/github/spec-kit) para desenvolvimento especification-driven em português.

### Instalação

1. **Instale o Specify CLI** (se ainda não tiver):
   ```bash
   uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
   ```

2. **Inicialize um projeto** com o Spec Kit:
   ```bash
   specify init meu-projeto --ai opencode
   cd meu-projeto
   ```

3. **Substitua os templates pelos em português**:
   ```bash
   cp -r /caminho/para/agents/speckit-ptbr/.specify/templates/* .specify/templates/
   ```

### Templates Disponíveis

- `spec-template.md` - Template para especificações de features
- `plan-template.md` - Template para planos de implementação
- `tasks-template.md` - Template para listas de tarefas
- `checklist-template.md` - Template para checklists de qualidade
- `agent-file-template.md` - Template para arquivos de agente

### Documentação Completa

Para mais detalhes sobre o fluxo de trabalho, visite a [documentação oficial do Spec Kit](https://github.com/github/spec-kit/blob/main/spec-driven.md).

## Requisitos

- [OpenCode](https://opencode.ai) ou agente compatível
- Node.js (para `npx skills` CLI)
- [uv](https://docs.astral.sh/uv/) (para Specify CLI)

## Licença

MIT
