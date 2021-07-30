# Banco de Dados  - MongoDB

### O que é um banco de dados?

Antigamente organizávamos nossos dados em papel e arquivos físicos, e com o tempo ficava bem difícil administrar essas informações. Além da dificuldade para lidar com essas informações, existia também um enorme risco de perdermos essa folha de papel que tinha nosso dado ou mesmo cair em mãos erradas. Hoje com um banco de dados conseguimos armazenar essas informações digitalmente, de forma segura, e recuperar muito mais facilmente os dados que precisamos, além de permitir que mais de uma pessoa acesse a mesma informação ao mesmo tempo, o que seria impossível com uma única folha de papel.

Em termos gerais, podemos definir banco de dados como uma coleção organizada onde se pode armazenar dados, de forma estruturada podendo ser consultada por um programa ou pessoa permitindo extrair informações. 

#### Banco de dados relacionais (SQL)

No banco de dados relacional nossas informações ficam em tabelas e se relacionam. Os bancos de dados relacionais são conhecidos como banco de dados SQL. Essa sigla SQL siginifica “Structured Query Language” que traduzindo para o português significa: “Linguagem de Consulta Estruturada”. Com o SQL, você pode executar vários comandos para criar, alterar, gerenciar, consultar, dentre outras informações no seu banco de dados. Costumamos dizer que bancos SQL seguem uma modelagem relacional, pois estes se baseiam no fato de que todos seus dados sejam guardados em tabelas.

#### Banco de dados não relacionais (noSQL)

Os bancos de dados NoSQL são, basicamente, bancos de dados que não são relacionais (SQL). O nome NoSQL já indica “Not Only SQL”. As *NoSQL databases* não precisam, necessariamente, ser parecidas entre si. São classificadas assim justamente por serem diferentes das relacionais. **Um exemplo de banco de dados de documentos é o famoso MongoDB!**

#### O que é o MongoDB?

MongoDB é um banco de dados não relacional (noSQL) orientado a documentos no formato JSON. Ele é opensource e possui alta performance e flexibilidade. Ao contrário de um banco de dados relacional (SQL), ele não possui como restrição a necessidade de ter as tabelas e colunas criadas previamente, permitindo que um ***documento*** represente toda a informação necessária, com todos os dados que você queira, no formato de um JSON. Esses documentos são agrupados em ***collections***, que em conjunto, forma um database (banco de dados).

#### Praticando :computer:

Para esse projeto, foi criado um json com o tema "Àlbuns da Beyoncé", no MongoDB com as seguintes rotas: pesquisa, inclusão, alteração e exclusão de itens.

![Are u ready?](https://3.bp.blogspot.com/-GPjvaR48_9c/VsoffARxRYI/AAAAAAAASh0/4RWLgEPL0kU/s1600/tumblr_nz7m8kgbHH1svlqpoo1_500.gif)



#### Demandas de negócio:

- Inserção de documentos;
- Atualização de documentos;
- Exclusão de documentos;
- Consulta com projeção;
- Consulta utilizando combinação entre os seletores;
- Consulta paginada e ordenada (utilizar skip, limit e sort).



#### Criando uma collection

`db.createCollection('albuns-estudio')`

#### Buscando um álbum

`db.getCollection('albuns-estudio').find({"nome": "LEMONADE"})`

#### Atualizando *single* de um álbum

`db.getCollection('albuns-estudio').update(
    
    {
        "nome" : "4"
    },
    

    
    {
        $set:{"singles": "1+1"}
    },
    
     
    {
        "multi" : false
       
    }
);`

#### Organizando os álbuns do mais recente ao mais antigo

`db.getCollection('albuns-estudio').find({"cantora": "Beyoncé"}).sort({ano: -1})`

#### Removendo um álbum

`db.getCollection('albuns-estudio').remove({"nome": { $ne: "I am... Sasha Fierce"}})`

#### Àlbuns com mais de 18 faixas

`db.getCollection('albuns-estudio').find({"cantora": "Beyoncé", "faixas":{$gt:18} })`

#### Álbum com a menor quantidade de faixas

`db.getCollection('albuns-estudio').find({"cantora": "Beyoncé"}).sort({faixas: 1}).skip(1).limit(1)`



![beyonce](https://2.bp.blogspot.com/-goLkPUhrusE/WNQBWhuQ-QI/AAAAAAAAZr8/hqQ1ul59sjkrI8ZRq6NYKRXsKdnQez70ACLcB/s1600/20%2BGifs%2BBeyonc%25C3%25A9%2B1.gif)











