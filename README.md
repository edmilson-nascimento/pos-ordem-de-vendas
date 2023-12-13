# Pos Ordem de Vendas #


Tratar dados para persistir apos salvar Ordem de Vendas.

![Static Badge](https://img.shields.io/badge/development-abap-blue)
![GitHub commit activity (branch)](https://img.shields.io/github/commit-activity/t/edmilson-nascimento/pos-ordem-de-vendas)


## Necessidade ##
Alguns dados de `tabelas Z` vão ser tratados e salvos apos a criação da _Ordem de Vendas_, ou seja, não é possível salvar as informações antes que a _Ordem_ seja salva e verificada no banco de dados.

Afim de evitar códigos que fiquem aguardando por tempo e fazendo demasiadas busca no banco de dados, será criada uma solução que faz uso dos recurso de chamadas de diferentes tipo de `funções` chegando uma alternativa mais **performatica e limpa** se tratando do ponto de vista de arquitetura de sistema SAP. Eu não sei como e quando foi criada a solução, mas quem me ajudou com esse assunto foi o [Murilo](mailto:murilo@abapconsulting.com.br) ~~uma das pessoas mais perfeccionistas que conheço~~ sempre buscando melhorar a qualidade do desenvolvimento.

Lembrando que dependendo do que você fizer isso vai bloquear edição na Ordem de Vendas logo em seguida, ou seja, se você precisa após uma alteração atualizar alguma coisa na Ordem de Vendas por esse comando ai vai gerar bloqueio.

## Tecnologia adotada ##
A solução consiste em criar duas funções, ambas com a mesma assinatura mas com tipos diferentes e automaticamente com chamadas diferentes. A chamada da primeira função é feita em uma exit e um processo vai desencadear outro.


## Solução ##

Função 1: Deve ser chamada em UPDATE TASK
Módulo de atualização + início retardado
Dentro da função 1 chamar a função 2 com os mesmos parametros.

Função 2: (cópia da 1) e deve ser chamada em STARTING NEW TASK
Módulo de acesso remoto + início imediato
Dentro da função 2 deve conter a lógica que precisa ser executada. Lembrando que nessa hora todos os dados da transação já foram gravados no BD.

![image](https://user-images.githubusercontent.com/22348098/151674787-7f454f5b-8332-4994-ae52-7d1d18339be8.png)

![image](https://user-images.githubusercontent.com/22348098/151674810-9e565904-a98a-4994-b07e-2ffd339cf7f1.png)

![image](https://user-images.githubusercontent.com/22348098/151674812-01eed82a-c767-46d6-bcff-478ff63f927c.png)

![image](https://user-images.githubusercontent.com/22348098/151674825-a33e7b21-3409-462c-bc11-373ba695fcf3.png)

![image](https://user-images.githubusercontent.com/22348098/151674837-b44c7a0c-43a4-460e-8672-d9cc433b1784.png)
