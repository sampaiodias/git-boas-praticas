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

## Commit

Cada commit é uma "fotografia" do repositório, agrupando um conjunto de alterações no software. Fazer um commit é a tarefa mais rotineira durante o desenvolvimento, sendo talvez a mais crítica de atenção também.

### Propósito único

Cada commit deverá ser responsável por uma única alteração no software: uma nova funcionalidade, uma correção, etc. Uma tarefa grande demais deverá ser quebrada em pequenas atividades, onde cada uma delas será registrada em um commit.

- :heavy_check_mark: Commit possui poucas alterações com um único propósito, alterando ou adicionando poucos arquivos.
- :x: Commit possui vários arquivos alterados e adicionados (mais de 10) e implementa duas ou mais funcionalidades.

### Mensagem clara

A mensagem (ou título) deverá explicar de forma susinta e objetiva o propósito do commit. Sem que seja necessário olhar cada alteração feita no commit, outro membro da equipe deverá ser capaz de ter pelo menos uma boa ideia do que foi feito simplesmente ao olhar sua mensagem.

- :heavy_check_mark: Mensagem com nome significativo e objetivo, como "Corrigido tema escuro da página inicial".
- :x: Mensagem muito grande ou com nome pouco explicativo, como "Correções gerais" ou "Implementado sistema de configuração da aplicação com a correção de X, Y e Z funcionalidades da tela inicial após discussão interna da equipe em preparação para a próxima Sprint".
- :nerd_face: Tente também manter sua mensagem entre 40 e 72 caracteres.

### Evitando conflitos

Em um ambiente mais de um desenvolvedor trabalha em um mesmo repositório ao mesmo tempo, alguns cuidados simples poderão evitar muita dor de cabeça no futuro ao evitar conflitos (alterações em um mesmo arquivo tentam se "juntar" sem sucesso).

- :heavy_check_mark: Cada desenvolvedor tenta sempre alterar apenas os arquivos que outros desenvolvedores não estejam alterando no momento.
- :x: Cada desenvolvedor altera e/ou apaga qualquer arquivo para atender a necessidade de sua tarefa.
- :nerd_face: Ao ver a necessidade de alterar um arquivo criado ou atualmente usado por outro desenvolvedor, pergunte-o sobre a possibilidade de alterar o(s) arquivo(s) para entrarem em um consenso sobre a melhor maneira de fazê-lo evitando conflitos.

## Branch

## Git Flow
