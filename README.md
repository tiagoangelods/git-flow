# git-flow

You can use git flow to manage your project's workflow, both personally and in a team. Think of git flow as a model, a strategy to organize your project's workflow. It is recommended to use git flow for applications that need to control multiple versions of the project. For example, a project that is in production and you need to fix a bug, but you cannot update the entire project version.

![Git Flow](./assets/gitflow.webp)

## Branches

- **main**: This is the main branch of the project, where the most stable version of the project resides.

- **develop**: This is the development branch, where features are developed and tested.

- **hotfix**: This is the branch where bugs are fixed.

- **feature**: This is the branch where features are developed.

- **release**: This is the branch where the project version is prepared for release.

## Installation

  - OSX: `brew install git-flow`
  - Linux: 
    - Debian: `apt install git-flow`
    - Arch: `gitflow-avh` on package manager
  - Windows: https://git-scm.com/download/win → Already included in Git from version 2.5.3 onwards.


## Starting git flow

To start git flow, you need to be on the main branch of the project, which is usually `main` or `master`.

```bash
git flow init
```
The result will look something like this:

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
### Creating a new feature

To create a new feature, you need to be on the `develop` branch.

```bash
git flow feature start feature-name
```

This command is equivalent to the basic git command:

```bash
git checkout develop
git checkout -b feature-name
```

### Finishing a feature

To finish a feature in git-flow, execute the following command:

```bash
git flow feature finish feature-name
```

This command is equivalent to the basic git command:

```bash
git checkout develop
git merge feature-name
```
## Hotfixes

### Creating a hotfix

```bash
git flow hotfix start hotfix-name
```

This command creates a new branch called `hotfix/hotfix-name` from the `main` branch. The above command is equivalent to:

```bash
git checkout main
git checkout -b hotfix/hotfix-name
```

### Finishing a hotfix

```bash
git flow hotfix finish hotfix-name
```

This command merges the `hotfix/hotfix-name` branch into both the `main` and `develop` branches. The above command is equivalent to:

```bash
git checkout main
git merge hotfix/hotfix-name
git checkout develop
git merge hotfix/hotfix-name
git tag hotfix-name
git branch -d hotfix/hotfix-name
```
## Releases

### Creating a release

```bash
git flow release start release-name
```

This command creates a new branch called `release/release-name` from the `develop` branch. The above command is equivalent to:

```bash
git checkout develop
git checkout -b release/release-name
```

### Finishing a release

```bash
git flow release finish release-name
```

This command merges the `release/release-name` branch into both the `main` and `develop` branches. The above command is equivalent to:

```bash
git checkout main
git merge release/release-name
git checkout develop
git merge release/release-name
git tag release-name
```

## Extras
