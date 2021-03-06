# Guia de Boas Práticas para Git

Este guia foi criado para ajudar o versionamento de software utilizando o Git, especialmente para equipes e organizações que queiram organizar e padronizar melhor seu fluxo de desenvolvimento. As "regras" aqui mencionadas abrangem os padrões mais usados pela comunidade, mas podem ser quebradas por sua equipe/organização caso possuam um bom motivo para tal.

As imagens usadas neste guia são feitas utilizando a ferramenta [GitKraken](https://www.gitkraken.com/invite?referralCode=6CFY7pSQ) para fins didáticos. As mesmas operações podem ser feitas na linha de comando ou com (quase) todos os outros clientes Git.

Legenda:
- :heavy_check_mark: Boa prática, faça sempre!
- :x: Exemplo de má prática, não faça!
- :nerd_face: Sugestão do autor. Faça se a equipe/organização toda concordar em fazer o mesmo.

## Sumário

1) [Repositório](#repositório)
2) [Commit](#commit)
3) [Branch](#branch)
4) [Git Flow](#git-flow)

## Repositório

Assim como você já deve saber, o repositório é onde os arquivos da sua aplicação ficam armazenados e versionados. Talvez por ser algo tão básico, alguns desenvolvedores acabam não cuidando de seu repositório da forma adequada, provocando não só desorganização mas muitas vezes conflitos que podem custar horas valiosas à sua equipe. Não deixe isso acontecer justamente com o "alicerce" do versionamento do seu projeto.

- :heavy_check_mark: Caso você seja administrador do repositório, controle o acesso às funcionalidades que podem ser executadas no repositório remoto (ex.: realizar merges para a branch master).
- :heavy_check_mark: Não envie arquivos de build, temporários ou de sua IDE para o repositório remoto. Para isso, adicione as devidas pastas e tipos de arquivo no arquivo ".gitignore". Uma boa versão inicial deste arquivo pode ser encontrada [clicando aqui](https://github.com/github/gitignore).
- :heavy_check_mark: Caso o seu repositório esteja disponível publicamente, não deixe de colocar um arquivo de licença apropriado na pasta raíz do seu repositório, sendo este arquivo um arquivo de texto simples com o nome 'LICENSE' (sem aspas e sem extensão de arquivo).
- :nerd_face: Se a sua aplicação utiliza arquivos grandes (10MB ou mais) no versionamento, considere a utilização do Git LFS. Porém, atente-se antes ao suporte e preços da utilização desta ferramenta no site em que você hospeda seu repositório.

<p align="center">
  <img src="img/git-init.png" />
</p>

## Commit

Cada commit é uma "fotografia" do repositório, agrupando um conjunto de alterações no software. Fazer um commit é a tarefa mais rotineira durante o desenvolvimento, sendo talvez a mais crítica de atenção também.

<p align="center">
  <img src="img/commits.png" />
</p>

### Propósito único

Cada commit deverá ser responsável por uma única alteração no software: uma nova funcionalidade, uma correção, etc. Uma tarefa grande demais deverá ser quebrada em pequenas atividades, onde cada uma delas será registrada em um commit.

- :heavy_check_mark: Commit possui poucas alterações com um único propósito, alterando ou adicionando poucos arquivos.
- :x: Commit possui vários arquivos alterados e adicionados (mais de 10) e implementa duas ou mais funcionalidades.

### Mensagem clara

A mensagem (ou título) deverá explicar de forma susinta e objetiva o propósito do commit. Sem que seja necessário olhar cada alteração feita no commit, outro membro da equipe deverá ser capaz de ter pelo menos uma boa ideia do que foi feito simplesmente ao olhar sua mensagem.

- :heavy_check_mark: Mensagem com nome significativo e objetivo, como "Corrigido tema escuro da página inicial".
- :heavy_check_mark: Começe a mensagem com letra maiúscula e termine-a sem ponto final.
- :x: Mensagem muito grande ou com nome pouco explicativo, como "Correções gerais" ou "Implementado sistema de configuração da aplicação com a correção de X, Y e Z funcionalidades da tela inicial após discussão interna da equipe em preparação para a próxima Sprint".
- :nerd_face: Tente também manter sua mensagem entre 40 e 72 caracteres.
- :nerd_face: Caso a equipe trabalhe com atividades que possuem um ID, considere a possibilidade de usar o ID como prefixo das mensagens dos commits. Por exemplo, "[HU001] Corrigido tema escuro da página inicial".

<p align="center">
  <img src="img/staging.png" />
</p>

### Evitando conflitos

Em um ambiente onde mais de um desenvolvedor trabalha em um mesmo repositório ao mesmo tempo, alguns cuidados simples poderão evitar muita dor de cabeça no futuro ao evitar conflitos (alterações em um mesmo arquivo tentam se "juntar" sem sucesso).

- :heavy_check_mark: Cada desenvolvedor tenta sempre alterar apenas os arquivos que outros desenvolvedores não estejam alterando no momento.
- :x: Cada desenvolvedor altera e/ou apaga qualquer arquivo para atender a necessidade de sua tarefa.
- :nerd_face: Ao ver a necessidade de alterar um arquivo criado ou atualmente usado por outro desenvolvedor, pergunte-o sobre a possibilidade de alterar o(s) arquivo(s) para entrarem em um consenso sobre a melhor maneira de fazê-lo evitando conflitos.

### Pull e Push

Para receber (pull) e enviar (push) commits do repositório remoto, também existem algumas práticas que tornam o fluxo de trabalho em equipe mais produtivo e seguro.

- :heavy_check_mark: Após terminar uma atividade, teste o software para garantir que tudo esteja funcionando corretamente. Feito isso, faça o push logo após a criação do commit.
- :heavy_check_mark: Caso outra pessoa esteja trabalhando na mesma branch, será necessário fazer o pull do repositório antes de fazer o push. Eventuais conflitos poderão aparecer (vide tópico anterior), resolva-os antes de prosseguir.
- :x: Criar um ou mais commits sem enviá-los ao repositório remoto.
- :x: Criar commits sem testar o software devidamente, correndo o risco de atrapalhar a equipe ao fazer o push.

## Branch

Uma branch de um repositório é uma "ramificação" da linha-do-tempo do projeto a partir de um determinado ponto, permitindo encapsular mudanças e adições ao software até que ele esteja pronto para se juntar à ramificação principal. Esse é um recurso extremamente importante e útil do Git, mas que pode gerar confusões ao ser usado erroneamente.

<p align="center">
  <img src="img/branches.png" />
</p>

### Múltiplas branches

Para softwares criados em equipe, é praticamente imprescindível que o desenvolvimento seja feito em várias branches que são atualizadas diariamente em paralelo.

- :heavy_check_mark: Cada membro (ou ao menos parte da equipe) trabalha em branches separadas, geradas a partir de outra branch (como a 'master' ou 'develop').
- :heavy_check_mark: Cada branch criada representa uma funcionalidade que é desenvolvida para o software.
- :x: Todos trabalham em uma única branch, seja ela a 'master' ou a 'develop'.
- :nerd_face: Crie uma branch secundária (usualmente chamada de 'develop') para agrupar as últimas adições feitas pela equipe.

### Nomenclatura

Não existe um padrão único de nomenclatura de branches na comunidade Git, mas algumas boas práticas costumam aparecer em todas.

- :heavy_check_mark: Nome da branch é significativo, ajudando a entender qual o propósito daquela branch.
- :heavy_check_mark: Nome da branch é curto, geralmente com até 20 caracteres.
- :heavy_check_mark: Nome de todas as branches seguem kebab case ou camel case.
- :x: Nome da branch contém o nome do desenvolvedor responsável por ela.
- :x: Nome da branch possui siglas não usuais (ex.: 'funcEnvioTarefa').

### Merge

Quando uma funcionalidade estiver pronta ou em um estágio que é necessário juntá-la ao resto do software, um merge (ou junção) da branch com outra branch deverá ser feita. Esta é uma ação importante e que requer especial atenção, já que um merge mal planejado pode consumir horas de trabalho ao tentar resolver conflitos inesperados.

- :heavy_check_mark: Planeje e comunique os merges com sua equipe. Todos devem estar cientes do que está sendo juntado e quando isso será feito.
- :heavy_check_mark: Após feito o merge, resolva os eventuais conflitos que aparecerem e teste o software antes de fazer o push das alterações locais feitas pelo merge. Caso desejado, é possível desfazer o merge antes de realizar seu envio para repositório remoto (push).
- :nerd_face: Realize os merges primeiramente numa branch secundária (ex.: 'develop') e, em certos intervalos de tempo, faça o merge da branch secundária para a branch principal, sinalizando uma nova versão em produção.

<p align="center">
  <img src="img/conflict.png" />
</p>


## Git Flow

O GitFlow é um fluxo de trabalho criado por [Vicent Driessen](https://nvie.com/posts/a-successful-git-branching-model/) em 2010 e é considerado por muitos o workflow de git mais adotado, e por um bom motivo. Assim como o este guia, o GitFlow tem como um de seus propósitos um versionamento mais fácil e seguro através da adoção de boas práticas comuns à equipe. Algumas dicas simples são o suficiente para que você acompanhe sua equipe neste workflow.

<i>Dica: Para um resumo dos comandos mais importantes do Git Flow, [clique aqui](https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html).</i>

- :heavy_check_mark: O Git Flow precisa ser iniciado (<i>git flow init</i>) em cada repositório local, e não apenas uma única vez para todos os membros da equipe. Por isso, inicialize o Git Flow com as configurações usadas pela equipe antes de usá-lo.
- :heavy_check_mark: Caso você esteja em uma equipe que usa Git Flow, certifique-se de aprender pelo menos os [comandos mais importantes](https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html) (tanto na linha de comando quanto no seu cliente Git de preferência, se houver suporte).
- :heavy_check_mark: Ao criar outras branches com o Git Flow (feature, hotfix ou release), use a nomenclatura de branches usada pela equipe (vide tópico de [Nomenclatura de Branches](#nomenclatura)).
- :heavy_check_mark: Caso a equipe utilize o Git Flow, use os comandos do próprio Git Flow para fazer a criação e finalização de features, hotfixes e releases. Isso é importante pois cada comando do Git Flow [executa um ou mais comandos git em sequência](https://gist.github.com/JamesMGreene/cdd0ac49f90c987e45ac).
- :heavy_check_mark: Se necessário, faça manualmente um merge da develop ou outra feature para a sua branch para obter atualizações importantes para a realização da sua tarefa.
- :nerd_face: Em casos excepcionais, é possível criar features a partir de outras branches que não seja a develop (exemplo: <i>git flow feature nome-da-nova-feature feature/branch-de-origem</i>).
- :nerd_face: É possível também finalizar as branches do Git Flow com um rebase. Como esse não é o comportamento padrão do Git Flow, faça desta forma apenas quando for o padrão adotado pela equipe.

<p align="center">
  <img src="img/git-flow.png" />
</p>

<p align="center">
  <img src="img/feature-start.png" />
</p>
