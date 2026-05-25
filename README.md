# Lab — Trunk-Based Development

**DevOps I · Aula 11.1 · Unidade 2**

---

## O que é Trunk-Based Development?

Trunk-Based Development (TBD) é um workflow onde todos os desenvolvedores integram código na branch principal (`main`) com alta frequência — várias vezes por dia. Branches são de vida muito curta (horas, no máximo 1 dia).

```
main  ──●──●──●──●──●──●──●──●──  (integração contínua, várias vezes ao dia)
          \  /    \  /
short      ●        ●              (branches de vida curta — horas)
```

### Princípios

| Princípio | Detalhe |
|-----------|---------|
| **Integração frequente** | Commits chegam à `main` várias vezes ao dia |
| **Branches curtas** | Máximo de 1 dia de vida — se demorar mais, está errado |
| **Feature flags** | Código incompleto pode ir para `main` desabilitado por flag |
| **Testes como guardião** | A `main` só aceita código que passa nos testes |

### Comparação com os outros workflows

| Aspecto | GitHub Flow | Git Flow | Trunk-Based |
|---------|-------------|----------|-------------|
| Branches longas | Sim | Sim | Não |
| Número de branches | Moderado | Alto | Mínimo |
| Frequência de integração | Por feature | Por sprint | Diária/horária |
| Indicado para | Times médios | Releases versionadas | Times maduros/CD |

---

## Exercício — Contribuição rápida ao trunk

A regra desta aula: **você tem 20 minutos para criar a branch, adicionar seu perfil e integrar na `main`.**

### Passo 1 — Clone o repositório

```bash
git clone git@github-univertix:alanrpereira88/lab-aula11-trunk-based.git
cd lab-aula11-trunk-based
```

### Passo 2 — Crie uma branch de vida curta

```bash
git switch main
git pull
git switch -c short/seu-nome-perfil
```

> Prefixo `short/` indica branch de vida curta (Trunk-Based).

### Passo 3 — Adicione seu perfil

```bash
cp time/_template.md time/seu-nome.md
```

Edite `time/seu-nome.md`. Mantenha simples — o objetivo é integrar rápido.

### Passo 4 — Commit, merge e push em sequência

```bash
git add time/seu-nome.md
git commit -m "feat: adiciona perfil de [Seu Nome]"

git switch main
git merge short/seu-nome-perfil
git branch -d short/seu-nome-perfil
git push origin main
```

> No TBD o merge é direto (fast-forward). Sem PR longo, sem revisão burocrática.

---

## Reflexão após o exercício

Responda no seu perfil (`time/seu-nome.md`), adicionando uma seção:

```markdown
## Reflexão — Trunk-Based

- O que foi diferente em relação ao GitHub Flow?
- Qual workflow te parece mais seguro? Por quê?
- Em que tipo de projeto você usaria cada um?
```

Commite a reflexão como um segundo commit na `main`.

---

## Entrega

- Print do `git log --oneline --graph --all` com seus commits na `main`
- URL do repositório

---

## Estrutura do repositório

```
lab-aula11-trunk-based/
├── README.md            ← você está aqui
├── CONTRIBUTING.md      ← regras de contribuição
├── docs/
│   ├── sobre-o-projeto.md
│   └── feature-flags.md ← leitura complementar
└── time/
    ├── _template.md     ← copie este arquivo
    └── alan-pereira.md  ← exemplo do professor
```
