# Dissertaçao tecnica
Prezados, irei fazer uma dissertacao tecnica do desafio proposto, tendo em vista que o
nivel de codificaçao e design patterns por mim utilizados ja e de vosso conhecimento.
    
* Base A
 
    Os requisitos da Base A, sao segurança e dados sensiveis. Levando em consideraçao um problema
    semelhante que ja enfrentei com o GDPR(EUROPA), os dados sensiveis podem ser armazenados em uma arquitetura NoSQL ou SQL, isso e irrelevante, dado a ncessidade da seguranaça
    utilizaria BlockChain para fazer uma criptografia simetrica dos dados, antes de inserir, e sempre que for necessario o resgate dos dados utilizar uma funçao serverless, pode ser o 
    Lambda(AWS) para decryptar o datasource solicitado, utilizando Python e Pandas por exemplo.
   
* Base B

    Neste caso, a forma que eu idealizei e de utilizar um serviço de streaming Apache Kafka por exemplo,
    tendo esses dados armazenados em um banco de dados, quando solicitado o score, o serviço ira inserir o no kafka uma mensagem com o identificador do usuario,
    um serviço serveless, ira receber a mensagem, resgatar os dados, transformar em um dataframe do pandas, classificar os mesmos de acordo com as regras de negocios definidas 
    e logo apos isso, inserir em uma outra fila no kafka o score gerado para que um outro serviço serveless apenas fizesse as alteraçoes de banco, e definir num banco de chave e valor, por exemplo REDIS, que ficaria por um TTL pre definido com aquele calculo.
    Utilizando filas diferentes, para seguir o single responsibility principle. 
    O Kafka seria de particionamento escalavel, para que o processamento seja quase que imediato. Necessario fazer toda a configuraçao de controle de acessos com um VPC na AWS, utilizando os ip privados para manter uma alta segurança, o unico acesso externo seria para inserir a mensagem na primeira fila de acesso.
      
* Base C
    Nesse caso, para uma busca rapida dos dados inseridos, eu utilizaria a stack "Elassandra" ElasticSearch + Cassandra,
    utilizando o CPF como Primary Key principal do Cassandra, para requisitar todos os dados, necessarios daquele CPF especifico de forma mais perfomatica.
    E no caso de uma pesquisa mais livre, sem o PrimaryKey, utilizar o ElasticSearch para chegar nos dados necessario.
    
    
# Conclusao
Basicamente essas sao as tecnologias que eu usaria para resolver todas essas questoes, como ja foi demonstrado alguns codigos que ja fiz, resolvir fazer uma dissertacao tecnica sobre a soluçao.

Espero que possa ser util para o proposito desse desafio, tambem estou disposto a debater as solucoes.

OBS: Estou utilizando um teclado de padrao EUROPEU que nao ha acentos, por isso a ausencia deles.

    
