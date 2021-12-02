# Simular tcode MIRO (geração de dados de NF) #

[![N|Solid](https://wiki.scn.sap.com/wiki/download/attachments/1710/ABAP%20Development.png?version=1&modificationDate=1446673897000&api=v2)](https://www.sap.com/brazil/developer.html)

Tratar dados para persistir apos salvar Ordem de Vendas

## Necessidade ##
Alguns dados de tabelas Z vao ser salvos apos a



De acordo com os Pedidos de Compras (que são acessados pela `ME23N`), será criada _Entrada de Mercadoria_ pela transação `MIRO` e depois a _Nota Fiscal_ (que pode ser acessada pela transação `J1B3N`). Houve a necessidade de que, antes disso, seja feita apenas uma simulação e os dados da _Nota Fiscal_ fossem recuperados para uma verificação, entender se esta da maneira esperada a configuração de Impostos ~~ou sei la mesmo porque o funcional inventou isso viu~~.

## Tecnologia adotada ##
A criação da classe sera para atender a necessidade e provera os dados de _Nota Fiscal_ caso seja preciso alguma validação referente a impostos.

## Solução ##
