# Guia de contribuição

Este guia explica o fluxo de trabalho do repositório: como criar uma branch, fazer commits, abrir um Pull Request, revisar e juntar as mudanças na `main`.

## Terminologia

| Termo | O que é |
|---|---|
| **Repositório** | A pasta do projeto com todo o histórico de mudanças |
| **Clone** | Baixar uma cópia do repositório para o seu computador |
| **Branch** | Uma "linha de trabalho" separada. Você mexe nela sem afetar a `main` |
| **Commit** | Um "ponto salvo" com as mudanças e uma mensagem explicando o que mudou |
| **Push** | Enviar seus commits do computador para o GitHub |
| **Pull** | Trazer do GitHub as mudanças que outras pessoas fizeram |
| **Pull Request (PR)** | Um pedido para juntar sua branch na `main`, com revisão |
| **Merge** | Juntar a sua branch na `main` |
| **Squash** | Forma de juntar em que todos os seus commits viram **um só** na `main` |
| **Conflito** | Duas pessoas mudaram o mesmo trecho; o Git pede para você escolher qual fica |

## Fluxo de trabalho

Execute as etapas **sempre na sequência abaixo**.

### 1. Atualize a `main`

```bash
git switch main
git pull
```

### 2. Crie a sua branch

O nome segue o padrão `tipo/descricao-curta` (minúsculas, sem acento, com hífen):

```bash
git switch -c feat/pagina-sobre
```

| Tipo | Quando usar | Exemplo |
|---|---|---|
| `feat` | Página ou funcionalidade nova | `feat/carrossel-home` |
| `fix` | Correção de erro | `fix/menu-celular` |
| `style` | Só aparência (CSS) | `style/cores-header` |
| `refactor` | Reorganizar sem mudar o resultado | `refactor/css-botoes` |
| `docs` | Documentação e textos do repositório | `docs/readme-equipe` |
| `chore` | Configuração, estrutura, manutenção | `chore/estrutura-pastas` |

### 3. Veja o que você mudou

```bash
git status
git diff
```

`git status` lista os arquivos alterados. `git diff` mostra linha por linha o que mudou. Confira se só tem o que você queria.

### 4. Faça o commit

```bash
git add arquivo1.html css/main.css
git commit -m "feat: cria estrutura da página Sobre"
```

- Prefira `git add` com os **nomes dos arquivos**. Evite `git add .` sem antes olhar o `git status`.
- A mensagem do commit tem o formato `tipo: o que foi feito`:

| Ruim | Bom |
|---|---|
| `alterações` | `feat: cria estrutura da página Sobre` |
| `ajeitei o css` | `style: ajusta espaçamento do header` |
| `arrumando` | `fix: corrige link do menu no celular` |

Pode fazer vários commits na mesma branch. Cada um deve ter um objetivo.

### 5. Envie para o GitHub

Na primeira vez da branch:

```bash
git push -u origin feat/pagina-sobre
```

Nas próximas vezes, basta `git push`.

### 6. Abra o Pull Request

1. No GitHub, clique no botão verde **Compare & pull request** que aparece no repositório.
2. **Título do PR:** use o padrão `tipo: descrição`. **O título vira a mensagem do commit na `main`**, então escreva com cuidado. Exemplo: `feat: adiciona página Sobre`.
3. Preencha as seções do modelo que aparece (o que muda, por quê, páginas afetadas, como testar e como você explicaria na defesa).
4. Em **Reviewers**, escolha quem vai revisar.
5. Clique em **Create pull request**.

O Cloudflare gera automaticamente um **link de prévia** do seu PR, que aparece como comentário ou check na página do PR em 1 a 2 minutos. O revisor abre esse link para testar sem baixar nada.

### 7. Responda à revisão

- Se pedirem mudanças, **edite na mesma branch**, faça novos commits e rode `git push`. O PR atualiza sozinho.
- Quando resolver um comentário, clique em **Resolve conversation**.
- Não precisa abrir PR novo.

### 8. Merge

Com a aprovação, **a pessoa que abriu o PR** clica em **Squash and merge**. A branch é apagada sozinha.

### 9. Sincronize a `main` e reinicie o ciclo

```bash
git switch main
git pull
```

Para a próxima tarefa, comece de novo do passo 2 com **uma branch nova**. Não reaproveite a branch antiga.

## Como revisar o PR de outra pessoa

1. Abra o **link de prévia** do PR e teste no computador e no celular (ou reduza a janela para 360 px).
2. Na aba **Files changed**, leia o código. Para comentar uma linha, clique no `+` ao lado dela.
3. Peça ao autor para **explicar o que fez**. Isso treina todo mundo para a defesa, em que cada pessoa pode ser perguntada sobre qualquer parte do site.
4. Quando estiver tudo certo, clique em **Review changes → Approve**. Se houver problemas, escolha **Request changes** e explique de forma objetiva.
5. Responda em até **24 horas**.

