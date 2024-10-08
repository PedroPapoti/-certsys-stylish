# Regras para um Fluxo de Trabalho Eficiente com Git


## Para garantir que o uso do Git seja eficiente e organizado, aqui estão algumas práticas recomendadas que você deve seguir para manter a integridade do repositório e o fluxo de trabalho limpo e escalável:

1. Trabalhe em uma feature branch
Por que isso é importante?
Ao desenvolver em uma feature branch, você isola seu trabalho do branch principal, evitando interferências. Isso permite a criação de múltiplos pull requests sem confusão e protege a branch principal (como develop ou master) de receber código instável ou incompleto.
Leia mais sobre feature branch workflow.

2. Crie a branch a partir de develop
Por que isso é importante?
Iniciar sua feature branch a partir de develop garante que o código na master permaneça estável e pronto para produção. Essa prática facilita o processo de automação de releases, mesmo que alguns projetos possam não exigir essa abordagem.

3. Nunca faça push diretamente para develop ou master. Use um Pull Request Amigável
Por que isso é importante?
A prática de enviar diretamente para as branches principais pode introduzir código não revisado ou instável, comprometendo a estabilidade do projeto. Utilize sempre um pull request para garantir que as alterações sejam revisadas por outros desenvolvedores.

4. Mantenha sua branch de develop atualizada e faça rebase interativo antes de enviar sua feature branch.
Por que isso é importante?
O rebase permite que você integre mudanças da develop na sua feature branch de maneira organizada, aplicando seus commits no topo do histórico. Isso evita a criação de múltiplos commits de merge, resultando em um histórico mais limpo.
Saiba mais sobre merging vs rebasing.

5. Resolva conflitos durante o rebase antes de fazer o pull request
Por que isso é importante?
Resolvendo os conflitos enquanto faz o rebase, você garante que o código esteja pronto para ser revisado e integrado à branch principal, evitando problemas no momento do pull request.

6. Exclua a branch local e remotamente após a conclusão.
Por que isso é importante?
Ao excluir branches antigas, você mantém o repositório organizado e evita o acúmulo de branches obsoletas. As feature branches devem existir apenas durante o desenvolvimento ativo.

7. Antes de criar um pull request, certifique-se de que sua feature branch passa nos testes e no build.
Por que isso é importante?
Antes de integrar o código em uma branch estável, é crucial garantir que ele esteja funcional e não introduza falhas. Isso inclui passar por todos os testes unitários e garantir que a verificação de estilo de código (lint) seja respeitada, promovendo a legibilidade e consistência do código.

8. Utilize o arquivo .gitignore padronizado.
Por que isso é importante?
Esse arquivo contém uma lista de arquivos e pastas que não devem ser incluídos no repositório remoto, como configurações de IDEs e bibliotecas de dependências. Isso mantém o repositório limpo e focado apenas nos arquivos necessários.