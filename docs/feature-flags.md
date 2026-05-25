# Feature Flags — Leitura Complementar

## O que é uma feature flag?

Feature flag (ou feature toggle) é uma técnica que permite ativar ou desativar funcionalidades em produção sem fazer um novo deploy.

No Trunk-Based Development, feature flags resolvem um problema real:

> "Como eu envio código incompleto para a `main` sem quebrar o sistema?"

## Exemplo prático

Imagine que você está desenvolvendo uma nova tela de login. Ainda não está pronta, mas o código já está na `main`:

```python
# config.py
FEATURE_NOVA_TELA_LOGIN = False  # mude para True quando estiver pronto
```

```python
# views.py
from config import FEATURE_NOVA_TELA_LOGIN

def login_view():
    if FEATURE_NOVA_TELA_LOGIN:
        return render("nova_tela_login.html")
    return render("tela_login.html")  # versão atual
```

O código vai para produção, mas a nova tela fica invisível para os usuários até que a flag seja ativada.

## Por que isso importa no TBD?

Sem feature flags, você precisaria de branches longas para esconder código incompleto. Com flags, você integra cedo e frequentemente sem risco para os usuários.

## Ferramentas populares

- [LaunchDarkly](https://launchdarkly.com) — plataforma dedicada a feature flags
- [Unleash](https://unleash.github.io) — open source
- Variáveis de ambiente simples — funciona para projetos pequenos

## Para refletir

- Em que situação você usaria feature flags no seu projeto?
- Quais riscos existem se você esquecer de remover uma flag antiga?
