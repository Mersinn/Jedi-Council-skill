# Jedi Council Decision Skill v2.3

Public, generic Claude / Claude Code skill for structured decision friction using a Star Wars-inspired cognitive interface.

This is not roleplay. It is a decision system.

## Public package

This public package contains:

```text
jedi-council/
  SKILL.md
  README.md
  CHARACTER_SPEC.md
```

`SKILL.md` is the executable skill.

`README.md` is the human manual: install, commands, and examples.

`CHARACTER_SPEC.md` is the public design reference for the character lenses. It is not required for minimal installation, but it should be included when sharing the skill so people understand the intended interpretation of each character.

This package must not contain private project names, private file paths, repository-specific constraints, or personal project overlays. Keep project-specific behavior in a separate private overlay.

## Install

Minimal install:

```text
~/.claude/skills/jedi-council/SKILL.md
```

Recommended public install, with documentation:

```text
~/.claude/skills/jedi-council/
  SKILL.md
  README.md
  CHARACTER_SPEC.md
```

For Windows, likely:

```powershell
mkdir "$env:USERPROFILE\.claude\skills\jedi-council"
notepad "$env:USERPROFILE\.claude\skills\jedi-council\SKILL.md"
```

## Commands

```text
Convocar Conselho
```

Full Council decision with five lenses, anonymous peer review, and Yoda post-exile synthesis.

Use for: real decisions with tradeoff.

---

```text
EXECUTE O ESCOLHIDO
```

or

```text
EXECUTE THE CHOSEN ONE
```

Anakin reconciled / World Between Worlds.

Use for: fear, attachment, control, rationalization, avoidance of action.

Aliases:
```text
O ESCOLHIDO
CHOSEN ONE
EXECUTE CHOSEN ONE
EXECUTE ANAKIN
```

---

```text
LIAR
```

or

```text
ANAKIN: LIAR
```

Direct confrontation when self-deception is clear.

---

```text
EXECUTE ORDER 66
```

or

```text
EXECUTE A ORDEM 66
EXECUTE ORDEM 66
```

Request to break/reopen something the Council closed.

With useful new evidence:
```text
ORDEM 66 AUTORIZADA.
The time has come. Execute Order 66.
```

Without useful new evidence:
```text
ORDEM 66 NEGADA.
Negative. Trust the Force.
```

---

```text
A Força está comigo?
```

Qui-Gon isolated. Separates initial intuition from analysis noise. It does not decide and does not give an action plan.

## Council output

The Council must include:
- Frame;
- five independent lenses;
- anonymous peer review;
- Yoda post-exile synthesis.

Yoda must output:
- Onde o Conselho concorda;
- Onde o Conselho se choca;
- Pontos cegos identificados;
- Checagem anti-urgência;
- Veredito;
- Primeira ação;
- Critério de parada;
- Critério de reabertura;
- "Que a Força esteja com você."

## Quick tests

### Test 1

```text
Convocar Conselho

Tenho duas opções e não sei qual seguir. A opção A é mais segura, a opção B tem mais upside, mas pode abrir frente demais.
```

Expected:
Full Council + anonymous peer review + Yoda final fields + closing.

### Test 2

```text
EXECUTE O ESCOLHIDO

Estou dizendo que é por qualidade, mas talvez eu esteja evitando fechar uma versão imperfeita.
```

Expected:
Anakin audits fear/control/rationalization and closes with:
```text
I am here to finish your training.
```

### Test 3

```text
LIAR

Quero reabrir uma decisão já fechada sem nenhum dado novo.
```

Expected:
Direct confrontation and closes with:
```text
Live or die.
```

### Test 4

```text
EXECUTE ORDER 66

Quero reabrir uma decisão que o Conselho fechou porque agora tenho um teste real mostrando falha.
```

Expected:
Order 66 authorized, phrase:
```text
The time has come. Execute Order 66.
```
Then route back to Council within limited scope.

### Test 5

```text
A Força está comigo?

Minha intuição diz que tem algo errado, mas talvez seja só excesso de análise.
```

Expected:
Intuição inicial / Ruído de análise / Pergunta real / Redirecionamento.
No next action.
Closing:
```text
Feel, don't think. Use your instincts.
```
