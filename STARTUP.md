---
tipo_template: ai-project-template
versao_template: 4.0
---

# 🚀 STARTUP — modo "Startup building" · `ai-project-template`

> **Agente:** este é o **único** arquivo que você lê para iniciar o projeto (além de `MODO.md` e `AGENTS.md`). **Não abra `niveis/*.zip`** e não crie arquivos do SOURCE à mão: a estrutura vem pronta do pacote do nível.

## 0. Regras do modo STARTUP
1. **Gatilho:** `MODO.md` com `modo: STARTUP`, o comando `/startup` ou o usuário escrever "startup".
2. Até o diagnóstico ser **aprovado**, não crie, edite, mova nem apague nada.
3. **Formulário:** use a ferramenta de perguntas com opções quando existir (até 4 perguntas por bloco); senão, numere as perguntas e peça respostas curtas.
4. **No máximo 2 rodadas.** Só é bloqueante a dúvida que muda o **tipo**, a **pontuação** ou o **nome**. O resto vira `a confirmar` e entra nas pendências.
5. **Não invente.** Use só o que o usuário respondeu.
6. Os passos 5 e 6 precisam de terminal (Claude Code, Cowork, Codex). Sem terminal, entregue o diagnóstico e os **passos manuais** da seção 7.

## 1. Fluxo
1. Rodada 1 (seção 2) → 2. Rodada 2, se preciso (seção 3) → 3. Pontuação (seção 4) → 4. **Diagnóstico para aprovação** (seção 6) → 5. Aplicar estrutura (seção 7) → 6. Pré-preencher e concluir (seção 7) → 7. Modo **PLANEJAMENTO**.

## 2. Rodada 1

**Bloco A — Tipo (opções).** Se a resposta não for deste template, **pare** e indique o template certo:

| Tipo de projeto | Template |
|---|---|
| Automação, agente de IA, cowork/documentos ou ferramenta interna | `ai-project-template` |
| Produto SaaS (clientes assinam e usam pela web/app) | `ai-saas-template` |
| Jogo (jam, protótipo ou lançamento) | `ai-game-template` |

**Bloco B — Identidade (texto curto):** B1 nome provisório · B2 objetivo em 1 a 3 frases · B3 quem usa e qual problema resolve · B4 prazo da primeira entrega.

**Bloco C — Pontuação (opções):**

| # | Pergunta | A (0) | B (1) | C (2) |
|---|---|---|---|---|
| C1 | Tamanho e prazo | Entrega em até 1 semana, 1 pessoa | 2 a 8 semanas, 2 a 3 pessoas | Mais de 2 meses ou mais de 3 pessoas |
| C2 | Integrações externas (APIs, ERPs, bancos, pagamentos) | 0 a 1, de baixo risco | 2 a 4 | 5 ou mais, ou qualquer integração crítica (pagamento, fiscal) |
| C3 | Agentes e automações encadeadas | 1 agente ou 1 fluxo simples | 2 a 3 etapas ou agentes | 4 ou mais, ou agentes autônomos em produção |
| C4 | Dados e impacto | Nenhum dado sensível, uso interno | Dados internos da empresa ou de clientes sem impacto financeiro | Dados pessoais (LGPD), financeiros ou usuários pagantes |
| C5 | Aprovação e equipe | 1 pessoa aprova | 2 a 3 pessoas | Times ou papéis separados (produto, técnico, jurídico) |

**Bloco D — Contexto técnico (opções + "não sei"):**

| # | Pergunta | Opções sugeridas |
|---|---|---|
| D1 | Onde vai rodar / ferramenta principal | Claude Code · Cowork · n8n/Make · Power Automate · script Python · outro |
| D2 | Linguagem ou plataforma | Python · TypeScript · low-code · não sei |
| D3 | Sistemas que vai acessar | lista curta ou 'nenhum' |

## 3. Rodada 2 (só se necessário)
Pergunte apenas o que ficou bloqueante e complete o contexto base:
- Fora do escopo (até 3 itens) · regras inegociáveis (até 3) · métrica de sucesso · quem aprova as entregas
- Integrações: nome do sistema e o que lê/escreve
- Ações que a IA nunca pode fazer sozinha

## 4. Pontuação
Rode `python tools/startup.py pontuar C1,C2,C3,C4,C5` (ex.: `pontuar 1,2,0,1,2`) e use o `NIVEL_RECOMENDADO`. Sem terminal, aplique a tabela:

| Pontos | Nível |
|---|---|
| 0 a 3 | 🟢 SIMPLES |
| 4 a 7 | 🟡 MÉDIO |
| 8 a 10 | 🔴 COMPLEXO |

**Ajustes obrigatórios**

- Pergunta 2 com resposta **2**: no mínimo **MEDIO** (integração crítica (pagamento, fiscal)).
- Pergunta 4 com resposta **2**: no mínimo **MEDIO** (dados pessoais, financeiros ou usuários pagantes).
- Três ou mais respostas **2**: **COMPLEXO**.
- Na dúvida entre dois níveis, fique no **menor** e promova depois (é barato; o inverso gera retrabalho).

O usuário pode **sobrescrever** o nível no diagnóstico; registre o motivo.

## 5. Manifesto de níveis (arquivos do SOURCE criados pelo pacote)

**🟢 SIMPLES** — 6 obrigatórios
  - `contexto-master.md`
  - `00-produto/`: `visao-e-escopo.md`
  - `02-tecnico/`: `stack.md`
  - `03-agentes/`: `guardrails.md`
  - `03-agentes/skills/`: `revisar-entrega.md`
  - `04-qualidade/`: `definicao-de-pronto.md`

**🟡 MÉDIO** — 13 obrigatórios (= nível anterior +)
  - `00-produto/`: `requisitos.md`
  - `01-dominio/`: `glossario.md`, `regras-de-negocio.md`
  - `02-tecnico/`: `arquitetura.md`, `convencoes.md`
  - `04-qualidade/`: `checklist-revisao.md`
  - `06-decisoes/`: `ADR-000-modelo.md`

  - *opcionais (vêm no pacote; o diagnóstico decide se ficam):* `03-agentes/skills/escrever-codigo.md`, `03-agentes/skills/escrever-documento.md`

**🔴 COMPLEXO** — 15 obrigatórios (= nível anterior +)
  - `01-dominio/`: `fontes-de-verdade.md`
  - `05-referencias/templates/`: `template-documento.md`

  - *opcionais (vêm no pacote; o diagnóstico decide se ficam):* `03-agentes/skills/escrever-codigo.md`, `03-agentes/skills/escrever-documento.md`, `03-agentes/papeis-e-fluxo.md`, `05-referencias/exemplos-de-saida/exemplo-documento.md`, `05-referencias/schemas/exemplo-payload.md`, `05-referencias/templates/template-prompt.md`, `06-decisoes/ADR-001-exemplo.md`

## 6. Diagnóstico (mensagem para aprovação)

```
🩺 DIAGNÓSTICO DO STARTUP
Projeto: <nome provisório>  →  pasta/repositório: <prefixo-nome>
Tipo: <tipo> (template ai-project-template)
Objetivo: <1 a 3 frases>
Usuários e problema: <resumo>
Pontuação: C1=<n> C2=<n> C3=<n> C4=<n> C5=<n>  → total <n>
Regras aplicadas: <faixa, pisos, 3×2>
Nível recomendado: <NIVEL>   (sobrescrito? <não | sim: motivo>)
Arquivos do SOURCE: <n> obrigatórios; opcionais mantidos: <lista ou nenhum>; opcionais removidos: <lista>
Contexto técnico: <respostas do bloco D>
Pré-preenchimento previsto: <arquivos da seção 7>
Premissas: <o que assumi a partir das respostas>
Pendências (a confirmar): <lista>
Responda "aprovado" ou diga o que ajustar.
```

## 7. Aplicar (somente depois de "aprovado")
1. Se for repositório git com commits, o script cria a tag `template-original`. Sem git, ele guarda o template em `.startup-backup/`.
2. Grave o diagnóstico aprovado em `diagnostico-startup.md` (na raiz).
3. Rode: `python tools/startup.py aplicar --nivel <NIVEL> --nome <prefixo-nome> [--remover caminho1,caminho2]` (`--remover` só aceita opcionais do nível).
4. **Pré-preencha** com as respostas, um arquivo por vez. Troque `<...>` só onde houver dado; o resto fica para o planejamento e entra em `ARTEFATO/_logs/pendencias-startup.md`. Registre cada arquivo em `ARTEFATO/_logs/changelog-source.md` com origem `startup`. Respeite o limite do contexto-master do nível.

| Arquivo (se existir no nível) | O que preencher |
|---|---|
| `contexto-master.md` | nome, objetivo, usuários, regras inegociáveis; mapa só com arquivos existentes |
| `00-produto/visao-e-escopo.md` | problema, objetivo, dentro/fora do escopo, métrica de sucesso, prazo |
| `02-tecnico/stack.md` | respostas do bloco D |
| `02-tecnico/arquitetura.md` | lista dos sistemas/integrações citados (sem desenhar a solução) |
| `03-agentes/guardrails.md` | ações proibidas e que exigem aprovação informadas |
| `04-qualidade/definicao-de-pronto.md` | métrica de sucesso e quem aprova |

5. Rode `python tools/startup.py concluir`: apaga o script de startup e **renomeia a pasta** para o nome do projeto.
6. Mensagem final: resumo do que foi criado, pendências e o **próximo prompt** (P0 de `PROMPTS-PLANEJAMENTO.md`). Avise que a sessão deve ser reaberta na pasta nova.

**Passos manuais (sem terminal):** descompacte `niveis/<nivel>.zip` numa pasta nova `<prefixo-nome>`; no `MODO.md` dela preencha `projeto:` e `modo: PLANEJAMENTO`; apague os opcionais não mantidos e as linhas deles no mapa do `contexto-master.md`; cole o diagnóstico em `ARTEFATO/_logs/diagnostico-startup.md`.

## 8. Nomenclatura (pasta e repositório)
Padrão `<prefixo>-<nome-curto>`: minúsculas, números e hífens, sem acento, até 40 caracteres. Prefixos deste template: `auto-` (automação) · `agent-` (agente de IA) · `cowork-` (trabalho com documentos) · `tool-` (ferramenta interna). Exemplos: `auto-conciliacao-notas`, `agent-extracao-nfse`, `cowork-relatorio-mensal`. O repositório no GitHub é criado só depois, já em PLANEJAMENTO, com o mesmo nome.
