# Mobicar

Mobicar é uma empresa que deseja entrar no mercado de aluguéis de carros (sendo
assim, utiliza somente o tipo carros na API). Tendo em vista a necessidade de possuir
vários canais, solicitou uma aplicação mobile onde fosse possível cadastrar carros
detalhando a fabricante, modelo, ano e valor da FIPE. Além do cadastro, deve ser possível
consultar os carros cadastrados também.
Seguindo as boas práticas organizacionais, desenvolva esta aplicação mobile a ser usada.
Nela deve ser possível adicionar e remover novos veículos à lista, assim como editar
veículos já listados. O valor do carro deve ser obtido através da API indicada abaixo. Utilize
os wireframes para se guiar. Seu layout deve ser funcional, interativo e responsivo.
Features adicionais serão muito bem vindas e estão a critério do candidato.

## Links úteis:
- Telas: https://www.figma.com/file/RvGo7PHM5ea5HpDyXy5hxJ/Mobcar?node-id=0%3A1
- Protótipo: https://www.figma.com/proto/RvGo7PHM5ea5HpDyXy5hxJ/Mobcar?node-id=1%3A3&viewport=260%2C435%2C0.5091469287872314&scaling=scale-down&page-id=0%3A1
- API: https://deividfortuna.github.io/fipe/


# API e Endpoints:
A API disponibiliza seus dados de busca no formato JSON. Confira a URL base de acesso a API:
```sh
https://parallelum.com.br/fipe/api/v1
```
## Marcas
### Requisição:
Primeiro liste as marcas do tipo de veículo que você deseja, através da ação marcas e sem nenhum parâmetro:
```sh
GET: https://parallelum.com.br/fipe/api/v1/carros/marcas
```
### Resposta
```sh
{
    Array [
     0: Object
        nome: "Acura"
        codigo: "1"
     1: Object
        nome: "Agrale"
        codigo: "2"
     2: Object
        nome: "Alfa Romeo"
        codigo: "3"
     3: Object
        nome: "AM Gen"
        codigo: "4"
     4: Object
        nome: "Asia Motors"
        codigo: "5"
    ]
}
```

## Modelos
### Requisição:
Na sequencia você poderá obter a listagem de veículos de uma determinada marca, com o código da marca desejada. Por exemplo a marca VW - VolksWagen (59):
```sh
GET: https://parallelum.com.br/fipe/api/v1/carros/marcas/59/modelos
```
### Resposta
```sh
{
    Object
     anos: Array [
         0: Object
            nome: "32000 Gasolina"
            codigo: "32000-1"
         1: Object
            nome: "32000 Diesel"
            codigo: "32000-3"
         2: Object
            nome: "2022 Gasolina"
            codigo: "2022-1"
         3: Object
            nome: "2022 Diesel"
            codigo: "2022-3"
         4: Object
            nome: "2021 Gasolina"
            codigo: "2021-1"
         modelos: Array [
             0: Object
                nome: "AMAROK CD2.0 16V/S CD2.0 16V TDI 4x2 Die"
                codigo: 5585
             1: Object
                nome: "AMAROK CD2.0 16V/S CD2.0 16V TDI 4x4 Die"
                codigo: 5586
             2: Object
                nome: "AMAROK Comfor. CD 2.0 TDI 4x4 Dies. Aut."
                codigo: 8531
             3: Object
                nome: "AMAROK CS2.0 16V/S2.0 16V TDI 4x2 Diesel"
                codigo: 5748
             4: Object
                nome: "AMAROK CS2.0 16V/S2.0 16V TDI 4x4 Diesel"
                codigo: 5749
        ]
   ] 
}
```

## Anos
### Requisição:
Após escolher o veículo desejado é possível consultar os modelos e os anos disponíveis para uma futura consulta de preços. Por exemplo AMAROK High.CD 2.0 16V TDI 4x4 Dies.
```sh
GET: https://parallelum.com.br/fipe/api/v1/carros/marcas/59/modelos/5940/anos
```
### Resposta
```sh
{
    Array [
     0: Object
        nome: "2021 Diesel"
        codigo: "2021-3"
     1: Object
        nome: "2020 Diesel"
        codigo: "2020-3"
     2: Object
        nome: "2019 Diesel"
        codigo: "2019-3"
     3: Object
        nome: "2018 Diesel"
        codigo: "2018-3"
     4: Object
        nome: "2017 Diesel"
        codigo: "2017-3"
     5: Object
        nome: "2016 Diesel"
        codigo: "2016-3"
     6: Object
        nome: "2015 Diesel"
        codigo: "2015-3"
     7: Object
        nome: "2014 Diesel"
        codigo: "2014-3"
     8: Object
        nome: "2013 Diesel"
        codigo: "2013-3"
     9: Object
        nome: "2012 Diesel"
        codigo: "2012-3"
     10: Object
        nome: "2011 Diesel"
        codigo: "2011-3"
    ]
}
```
## Valor
### Requisição:
Por fim adicionando mais um parâmetro será possível visualizar o preço corrente da Tabela FIPE para este veículo/modelo/ano. Continuando com o exemplo a cima para obter o valor de um veículo do ano 2014 a Gasolina utilizaremos o id 2014-3:
```sh
GET: https://parallelum.com.br/fipe/api/v1/carros/marcas/59/modelos/5940/anos/2014-3
```
### Resposta
```sh
{
    Object
        Valor: "R$ 123.580,00"
        Marca: "VW - VolksWagen"
        Modelo: "AMAROK High.CD 2.0 16V TDI 4x4 Dies. Aut"
        AnoModelo: 2014
        Combustivel: "Diesel"
        CodigoFipe: "005340-6"
        MesReferencia: "dezembro de 2021 "
        TipoVeiculo: 1
        SiglaCombustivel: "D"
}
```

Baixe o instalador do app em 'apk/app-release.apk'
