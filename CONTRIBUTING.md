# Guia de Contribuição

## Workflow adotado: Trunk-Based Development

### Regra de ouro

> Nenhuma branch dura mais de 1 dia. Se ainda não terminou, use feature flag.

### Fluxo

```
main → short/nome → main (mesmo dia)
```

1. Crie a branch a partir da `main` atualizada
2. Faça o trabalho mínimo necessário
3. Faça merge de volta na `main` imediatamente
4. Delete a branch

### Nomenclatura de branches

```
short/nome-sobrenome-descricao
```

Exemplos:
- `short/joao-silva-perfil`
- `short/maria-santos-reflexao`

## Padrão de commits

Use [Conventional Commits](https://www.conventionalcommits.org/pt-br/):

```
<tipo>: <descrição curta em português>
```

## O que não fazer

- Não manter branch aberta por mais de 1 dia
- Não acumular mudanças grandes numa branch
- Não fazer merge sem antes rodar `git pull` na main
