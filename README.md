# 🧩 ai-project-template

> Template para automações, agentes de IA, cowork/documentos e ferramentas internas. Arquitetura **SOURCE / ARTEFATO**, modos **PLANEJAMENTO / EXECUÇÃO** e **3 níveis de complexidade** escolhidos automaticamente no *Startup building*.

## Como iniciar um projeto
1. No GitHub, **Use this template** → *Download ZIP* (ou clone) e abra a pasta **localmente**.
2. Abra o agente na pasta:
   - **Claude Code:** digite `/startup`
   - **Cowork / Codex / outros:** digite `startup`
3. Responda as perguntas (até 2 rodadas) e **aprove o diagnóstico**.
4. O agente cria a estrutura do nível, pré-preenche o SOURCE, renomeia a pasta (ex.: `auto-conciliacao-notas`, `agent-extracao-nfse`, `cowork-relatorio-mensal`) e entra em **PLANEJAMENTO**.
5. Termine o planejamento e só então suba o projeto para o GitHub com o mesmo nome.

## Níveis

| Nível | Exemplos | Arquivos no SOURCE |
|---|---|---|
| 🟢 SIMPLES | Automação pontual (robô de relatório), script, landing page, documento | 6 |
| 🟡 MÉDIO | Agente com integrações, MVP de SaaS, automação entre sistemas, app de uma área | 13 |
| 🔴 COMPLEXO | SaaS com clientes pagantes, vários agentes, integrações críticas, múltiplos times | 15 + opcionais |

## Estrutura do template
```
📦 ai-project-template/
├── 📄 README.md         → este arquivo (humanos)
├── 🚀 STARTUP.md        → instruções do Startup building (o agente lê só ele)
├── 🚦 MODO.md           → modo: STARTUP
├── 📄 AGENTS.md · CLAUDE.md · .claude/commands/startup.md
├── 📁 niveis/           → simples.zip · medio.zip · complexo.zip · niveis.json
├── 📁 tools/startup.py  → aplica o nível, renomeia a pasta, checa os pacotes
└── 📁 .github/workflows/checar-template.yml
```

## Uso manual (sem agente)
Baixe `niveis/<nivel>.zip`, descompacte numa pasta `<prefixo>-<nome>` e siga o `README.md` de dentro do pacote.

## Outros templates
`ai-saas-template`, `ai-game-template`

## Manutenção
Os pacotes são **gerados** pelo repositório `ai-template-factory` (`python build.py`). Não edite os zips à mão; o check `checar-template` falha se pacote, `niveis.json` e `STARTUP.md` divergirem.
