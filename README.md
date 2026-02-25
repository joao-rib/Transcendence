# Transcendence

## Instruções para feat/branches

Exemplo: Adicionar novas configs em backend

1. Entrar na branch base
  git checkout **backend**
1. Não esquecer de atualizar tudo
  git pull
1. Criar nova branch, localmente
  git checkout -b **feat/addednewconfigs**
1. Trabalhar em alterações desejadas dentro da nova branch
  *Alterar código, fazer vários commits, etc.*
1. Criar nova branch, remotamente
  git push -u origin **feat/addednewconfigs**
1. Reentrar na branch principal
  git checkout **backend**
1. Fazer merge localmente
  git merge **feat/addednewconfigs**
1. Resolver potenciais conflitos
  VSCode, vim, github, etc.
1. Fazer merge remotamente
  Criar pull request, pedir aprovação

Após aprovação do pull request, a nova branch é apagada remotamente de forma automática (se necessário, restaurá-la é possível).
Localmente, a nova branch ainda aparece. Para apagar a sua informação, entrar numa branch existente (ex.: backend) e efectuar os seguintes comandos:

1. git pull
1. git fetch --prune
1. git branch -d **feat/addednewconfigs**
  (se não deixar, tentar -D em vez de -d)

### cherry-picking

Para fazer merge apenas de commits específicas, usa-se o comando **git cherry-pick**

1. Obter hashes dos vários commits feitos numa branch específica
  git log --oneline **outrabranch**
1. Usar o(s) hash(es) obtidos para passar apenas as alterações desejadas
    2.1. Apenas um commit
      git cherry-pick **commit-hash**
    2.2. Vários commits
      git cherry-pick **commit-hash-1** **commit-hash-2** ... **commit-hash-N**
    2.3. Apenas um merge-commit
      git cherry-pick -m 1 **commit-hash**
    2.4. Vários merge-commits