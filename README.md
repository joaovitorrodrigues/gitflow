# CapitalGains

## Informações para execução do projeto

dentro da pasta `csharp`, execute os seguintes comandos:
    
### Acessar a pasta da solution 
    cd capitalgains

### Construir imagem da aplicação
    docker build -f capitalgains/Dockerfile -t capitalgains:dev .

### Construir imagem dos testes
    docker build -f capitalgainstests/Dockerfile -t capitalgainstests:dev .


### Para Execução da aplicação
opção 1:

    docker run  -it --rm capitalgains:dev
    ## depois, inserir os inputs manualmente.
      
opção 2:

    docker run -i capitalgains:dev < arquivo_json_com_multiplos_testes.json/txt



### Para execução dos testes
    docker run --rm capitalgainstests:dev



## Decisões técnicas, framework, etc.

-   Optei por usar docker porque os testes aparentemente serão no Unix ou Mac.

-   Escolhi o C# pois estou habituado a usá-lo diariamente. Optei pelo .NET 8 como framework porque além de ser LTS,
    ele também possui incluído a "System.Text.Json" que serve para manipular arquivos JSON sem a necessidade de um pacote adicional como o Newtonsoft.Json, por exemplo.

-   Optei por criar a entidade "Operations" dentro do arquivo Program.cs para não criar infraestrutura desnecessária como sugerido no arquivo pdf.

-   Optei pelos testes com MSTest pois é nativo do .NET 6.0+, então não existe a necessidade de pacotes adicionais como xUnit, por exemplo.

-   Sobre os testes, optei por criar um para a operação "buy" e cálculo da nova média. Para o lucro e imposto optei por um teste para cada com múltiplas entradas(positivo, negativo e
    zero para o lucro, e para o imposto/taxa operação menor que 20k, prejuízo e operação maior que 20k e pagando imposto).


