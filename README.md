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

Cada commit deverá ser responsável por uma unica alteração no software: uma nova funcionalidade, uma correção, etc. Uma tarefa grande demais deverá ser quebrada em pequenas atividades, onde cada uma delas será registrada em um commit.

- :heavy_check_mark: Commit possui poucas alterações com um único propósito, alterando ou adicionando poucos arquivos.
- :x: Commit possui vários arquivos alterados e adicionados (mais de 10) e implementa duas ou mais funcionalidades.

## Branch

## Git Flow
