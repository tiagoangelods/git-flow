# git-flow

Você pode utilizar git flow para gerenciar o fluxo de trabalho do seu projeto, tanto pessoal como em equipe.
Veja o git flow como um modelo, uma estraatégia para organizar o fluxo de trabalho do seu projeto.
Recomenda-se utilizar o git flow para aplicacões que precisam de ter um controle sobre várias versões do projeto, como por exemplo, um projeto que está em produção e você precisa corrigir um bug, mas não pode atualizar a versão do projeto inteira.

![Git Flow](./assets/gitflow.webp)

## Brahcnes

- **main**: É a branch principal do projeto, onde está a versão mais estável do projeto.

- **develop**: É a branch de desenvolvimento, onde as features são desenvolvidas e testadas.

- **hotfix**: É a branch onde os bugs são corrigidos.

- **feature**: É a branch onde as features são desenvolvidas.

- **release**: É a branch onde a versão do projeto é preparada para ser lançada.

## Instalação

  - OSX: `brew install git-flow`
  - Linux: 
    - debian: `apt install git-flow`
    - arch: `gitflow-avh` on package manager
  - Windows: https://git-scm.com/download/win → Já está incluído no Git a partir da versão 2.5.3.

## Iniciando o git flow

Para iniciar o git flow, você precisa estar na branch principal do projeto, que geralmente é a `main` ou `main`.

```bash
git flow init
```

O resultado será algo parecido com isso:

```bash
Which branch should be used for bringing forth production releases?
   - main
Branch name for production releases: [main] 
Branch name for "next release" development: [develop] 

How to name your supporting branch prefixes?
Feature branches? [feature/] 
Bugfix branches? [bugfix/] 
Release branches? [release/] 
Hotfix branches? [hotfix/] 
Support branches? [support/] 
Version tag prefix? [] 
Hooks and filters directory? [/projects-directory/.git/hooks]
```
## Features
### Criando uma nova feature

Para criar uma nova feature, você precisa estar na branch `develop`.

```bash
git flow feature start nome-da-feature
```

Este comando representa o mesmo que o comando básico do git:

```bash
git checkout develop
git checkout -b name-feature
```

### Finalizando uma feature

Para finalizar uma feature no git-flow, execute o seguinte comando:

```bash
git flow feature finish nome-da-feature
```

Este comando representa o mesmo que o comando básico do git:

```bash
git checkout develop
git merge name-feature
```
## Hotfixes

### Criando um hotfix

```bash
git flow hotfix start name-hotfix
```

Este comando cria uma nova branch chamada `hotfix/name-hotfix` a partir da branch `main`. Os comando acima é equivalente a:

```bash
git checkout main
git checkout -b hotfix/name-hotfix
```

### Finalizando um hotfix

```bash
git flow hotfix finish name-hotfix
```

Este comando faz o merge da branch `hotfix/name-hotfix` na branch `main` e na branch `develop`. Os comando acima é equivalente a:

```bash
git checkout main
git merge hotfix/name-hotfix
git checkout develop
git merge hotfix/name-hotfix
git tag name-hotfix
git branch -d hotfix/name-hotfix
```
## Releases

### Criando uma release

```bash
git flow release start name-release
```

Este comando cria uma nova branch chamada `release/name-release` a partir da branch `develop`. Os comando acima é equivalente a:

```bash
git checkout develop
git checkout -b release/name-release
```

### Finalizando uma release

```bash
git flow release finish name-release
```

Este comando faz o merge da branch `release/name-release` na branch `main` e na branch `develop`. Os comando acima é equivalente a:

```bash
git checkout master
git merge release/name-release
git checkout develop
git merge release/name-release
git tag name-release
```

## Extras
