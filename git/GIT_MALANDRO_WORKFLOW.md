# Git Workflow Certsys

Na Certsys, utilizamos o [Feature-Branch Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows#feature-branch-workflow) em conjunto com o [Interactive Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing#the-golden-rule-of-rebasing) e alguns elementos do [Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows#gitflow-workflow). Os principais passos são os seguintes:

### 1. Para um novo projeto :heart_eyes:

Inicialize um repositório Git no diretório do projeto:

```sh
cd <diretório do projeto>
git init
 ```


2. Crie uma nova branch de funcionalidade

```sh
git checkout -b <nome-da-branch>
 ```

3. Faça um commit campeão

```sh
git add .
git commit -a
```
Por que?
O comando git commit -a abrirá um editor que permite separar o assunto do corpo do commit, facilitando a documentação das mudanças.

5. Sincronize com o remoto
Para obter as alterações mais recentes:

```sh
git checkout develop
git pull
```
Por que?

Isso permite que você lide com conflitos localmente enquanto realiza o rebase, em vez de encontrar conflitos ao fazer o Pull Request.

5. Atualize sua branch de funcionalidade com as últimas alterações do develop
Utilize o rebase interativo:


```sh
git checkout <nome-da-branch>
git rebase -i --autosquash develop
```
Por que?
A opção --autosquash transforma todos os seus commits em um único commit. Evite ter muitos commits para uma única feature branch. Leia mais pequeno gafanhoto.

6. Resolva conflitos (se necessário)
Se houver conflitos, resolva-os e continue o rebase:

```sh
Copiar código
git add <file1> <file2> ...
git rebase --continue
```

7. Faça o Push da branch
Como o rebase reescreve o histórico do Git, será necessário utilizar a flag -f para forçar as mudanças no repositório remoto. Se outras pessoas estiverem trabalhando na branch, use a opção menos destrutiva --force-with-lease.

```sh
git push -f
```
Por que?
Quando você faz um rebase, está alterando o histórico da sua branch de funcionalidade. Portanto, o Git rejeitará o push padrão. Use a flag -f ou --force para forçar o push. Leia mais....

8. Faça um Pull Request Amigão
Os Pull Requests serão aceitos, mesclados e fechados pelo revisor.

9. Remova sua branch de funcionalidade
Após a aceitação do Pull Request, remova sua branch localmente:

```sh
Copiar código
git branch -d <nome-da-branch>
```
Para remover todas as branches que não estão mais no remoto, utilize:


```sh
Copiar código
git fetch -p && for branch in `git branch -vv | grep ': gone]' | awk '{print $1}'`; do git branch -D $branch; done
```


Sinta-se à vontade para colar isso no seu arquivo! Se precisar de mais alguma coisa, é só avisas