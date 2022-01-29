# Pos Ordem de Vendas #

[![N|Solid](https://wiki.scn.sap.com/wiki/download/attachments/1710/ABAP%20Development.png?version=1&modificationDate=1446673897000&api=v2)](https://www.sap.com/brazil/developer.html)
Tratar dados para persistir apos salvar Ordem de Vendas.

## Necessidade ##
Alguns dados de `tabelas Z` vão ser tratados e salvos apos a criação da _Ordem de Vendas_, ou seja, não é possível salvar as informações antes que a _Ordem_ seja salva e verificada no banco de dados.

Afim de evitar códigos que fiquem aguardando por tempo e fazendo demasiadas busca no banco de dados, será criada uma solução que faz uso dos recurso de chamadas de diferentes tipo de `funções` chegando uma alternativa mais **performatica e limpa** se tratando do ponto de vista de arquitetura de sistema SAP. Eu não sei como e quando foi criada a solução, mas quem me ajudou com esse assunto foi o [Murilo](mailto:murilo@abapconsulting.com.br) ~~uma das pessoas mais perfeccionistas que conheço~~ sempre buscando melhorar a qualidade do desenvolvimento.

Lembrando que dependendo do que você fizer isso vai bloquear edição na Ordem de Vendas logo em seguida, ou seja, se você precisa após uma alteração atualizar alguma coisa na Ordem de Vendas por esse comando ai vai gerar bloqueio.

## Tecnologia adotada ##
A solução consiste em criar duas funções, ambas com a mesma assinatura mas com tipos diferentes e automaticamente com chamadas diferentes. A chamada da primeira função é feita em uma exit e um processo vai desencadear outro.


## Solução ##

![image](https://user-images.githubusercontent.com/22348098/151674787-7f454f5b-8332-4994-ae52-7d1d18339be8.png)
