# Documentação: Branches e Commits Semânticos no Git

Repositório de testes: https://github.com/Prizzax300/teste-git-branches

## 1. Objetivo

Praticar a organização do desenvolvimento com **branches** e padronizar as mensagens de commit com o **Conventional Commits**, simulando um fluxo de trabalho em equipe.

## 2. O que são branches

Uma branch é uma linha independente de desenvolvimento, na prática um ponteiro leve para um commit. A branch **main** guarda a versão estável do projeto, a que pode ser entregue. As **branches de desenvolvimento** (feature branches) são criadas a partir da main para trabalhar em algo específico, como uma funcionalidade, uma correção ou a documentação. Quando o trabalho está pronto, ele é integrado (merge) à main e a branch pode ser apagada.

| | main | Branch de desenvolvimento |
|---|---|---|
| Objetivo | Versão estável | Trabalho em andamento |
| Vida útil | Permanente | Temporária |
| Alterações | Só via merge ou Pull Request | Feitas pelo responsável da tarefa |

## 3. Commits semânticos (Conventional Commits)

Padrão de mensagem no formato `tipo(escopo opcional): descrição curta`.

| Tipo | Uso | Exemplo |
|---|---|---|
| feat | Nova funcionalidade | feat: adiciona script de saudação |
| fix | Correção de bug | fix: corrige cálculo do total |
| docs | Documentação | docs: explica como executar o script |
| style | Formatação, sem mudar a lógica | style: adiciona comentário ao script |
| refactor | Reestruturação sem mudar o comportamento | refactor: separa função de validação |
| test | Criação ou ajuste de testes | test: adiciona testes do carrinho |

## 4. Comandos utilizados

### Configuração e criação do repositório

```bash
mkdir teste-git-branches
cd teste-git-branches
git init -b main
git config user.name "Seu Nome"
git config user.email "seu@email.com"
```

### Commit inicial na main

```bash
echo "# Projeto de Teste" > README.md
git add README.md
git commit -m "docs: adiciona README inicial"
```

### Criar e alternar de branch

```bash
git switch -c feat/saudacao
git branch
```

### Commits semânticos na branch

```bash
echo 'print("Olá, mundo!")' > saudacao.py
git add saudacao.py
git commit -m "feat: adiciona script de saudação"

echo "Execute com: python saudacao.py" >> README.md
git add README.md
git commit -m "docs: explica como executar o script"
```

### Integrar à main

```bash
git switch main
git merge --no-ff feat/saudacao -m "merge: integra branch feat/saudacao"
git branch -d feat/saudacao
```

### Publicar no GitHub

```bash
git remote add origin https://github.com/Prizzax300/teste-git-branches.git
git remote -v
git push -u origin main
```

### Visualizar o histórico

```bash
git log --oneline --graph --all
```

### Referência rápida

| Comando | Função |
|---|---|
| git branch | Lista as branches |
| git switch nome | Alterna para uma branch |
| git switch -c nome | Cria e alterna |
| git merge nome | Integra a branch na branch atual |
| git branch -d nome | Apaga a branch já integrada |

## 5. Evidências

Inserir aqui os prints:

- **Print 1:** saída de `git log --oneline --graph --all`, mostrando os commits semânticos e o merge da branch.
- **Print 2:** aba Commits do repositório no GitHub.
- **Print 3:** aba Pull requests ou Insights > Network, mostrando a branch integrada.

## 6. Como branches e commits semânticos ajudam o trabalho em grupo

### Branches

- **Isolamento:** cada pessoa trabalha na sua tarefa sem quebrar o código dos colegas.
- **Paralelismo:** várias funcionalidades evoluem ao mesmo tempo.
- **Segurança:** a main continua estável e pronta para entrega.
- **Revisão:** com Pull Requests, o código é revisado antes de entrar na main.
- **Rastreabilidade:** o nome da branch indica o propósito do trabalho.

### Commits semânticos

- **Histórico legível:** dá para entender o que mudou apenas lendo o `git log --oneline`.
- **Padronização:** toda a equipe escreve mensagens no mesmo formato.
- **Busca e filtragem:** `git log --grep="^feat"` lista só as funcionalidades.
- **Automação:** ferramentas geram changelog e definem versões a partir dos tipos.
- **Depuração mais rápida:** fica mais fácil localizar o commit que
