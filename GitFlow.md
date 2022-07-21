# Manual Pratico para Iniciar o Git Flow


Ao utilizar a biblioteca de extensão do git-flow, executar git flow init no repositório existente vai criar uma ramificações nos branchs de desenvolvimento:

Ao usar a extensão do git-flow, você será levado para uma configuração que requer alguns aceites e nomeação da estrutura de SCM conforme abaixo:


```
$ git flow init


Initialized empty Git repository in C:/Windows/System32/.git/
No branches exist yet. Base branches must be created now.
Branch name for production releases: [master]
Branch name for "next release" development: [develop]

How to name your supporting branch prefixes?
Feature branches? [feature/]
Bugfix branches? [bugfix/]
Release branches? [release/]
Hotfix branches? [hotfix/]
Support branches? [support/]
Version tag prefix? []


$ git branch
* develop
 main
```

#Iniciar Branchs e recurso

`git flow feature start feature_branch`

Continue seu trabalho e use o Git como de costume.

#No fim do desenvolvimento finalize o branch  de Feature

Quando você concluir o trabalho de desenvolvimento, a próxima etapa é fazer o Merge o branch de Feature na de desenvolvimento.

`git flow feature finish feature_branch`

#Ramificação do branch Release

Uma vez que o branch `develop` adquiriu `features` suficientes para um release (ou uma data de lançamento em produção predeterminada está se aproximando), você bifurca um branch `release` a partir da `develop`. 


```
$ git flow release start 0.1.0
Switched to a new branch 'release/0.1.0'
```
Depois que a versão estiver pronta para o lançamento em produção, vai ser feito o merge dela no branch `main/master` e no branch `develop` e, então, o branch `release` vai ser **excluído**.

O processo de merge de volta para o branch `develop` é importante porque atualizações importantes podem ter sido adicionadas ao `release` e elas devem ser acessíveis a novos recursos.
 este processo é tratado com a revisão de códigos através da abertura de [PullRequest

#Para finalizar a ramificação de lançamento, use os seguinte método:

`git flow release finish '0.1.0'`

Caso você esteja apenas fechando o branch, use o comando sem a extensão git flow ser for necessario:


```
git checkout main
git merge release/0.1.0
```

# Branchs de Hotfix

Os branchs de suporte/manutenção ou de “`hotfix`” são usados para corrigir com rapidez ****problemas** em produção**. Os branchs de hotfix se parecem muito com os de `release` e `feature`, com a diferença de serem baseados no branch `main/master` ao invés do branch `develop`.

##Para iniciar uma correção hotfix use;

`$ git flow hotfix start hotfix_branch`

Assim como acontece na finalização do branch `release`, é feito o merge do branch de `hotfix` tanto no `main/mater` quanto no `develop`.


```
git checkout main
git merge hotfix_branch
git checkout develop
git merge hotfix_branch
git branch -D hotfix_branch
```
## Para finalizar o branch hotfix use;

`$ git flow hotfix finish hotfix_branch`




