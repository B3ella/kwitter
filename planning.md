Trabalho de NoSQL
Clone do twitter
Ingestão de dados usando kafka
Usuários podem se cadastrar, se seguir e postar texto (talvez outras midias)

Neo4J pra redes de amigos e recomendações

Elastic search pra pesquisa por texto
Unbundled database, talvez outras otimizações de leitura pro feed por exemplo

HTTP handles scale very
well. However, HTTP is not good at low latency (where some message
brokers excel)
-building microservices

Atom Publishing Protocol

Python container

Começar com um sistema exemplo e substituir as tecnologias depois
  Clone do twitter:
    Usuários podem se cadastrar
    Fazer amigos
    Todos tem um perfil em que podem postar texto


Já tenho um broker kafka
daqui tem 2 tópicos
1 de usuários pra criação, alteração, seguir e deixar de seguir
    Cadastrar usuário
        Nome de usuário
        Senha
    Seguir usuário
        Nome do usuário seguido
        Nome do usuário seguindo
    Deixar de seguir usuário
        mesmo do de cima
    
1 de posts é o que controla o feed
    Nome do usuário publicando
    Texto do post
    id do post

Desses tópicos vamos derivar o grafo de recomendação usando Neo4J
Todos os posts também vão ser indexados num elasticsearch pra pesquisa

Acho que faz sentido começar a desenvolver pelos serviços que vão usar essas funções
Tô tendenciosa a começar pelo serviço de sign-up
Acho que uma ordem apropriada pra seguir depois seria
sign-in
Follow/unfollow
Ler feed
Full-text search
recommendations

Tô chamando eles de serviços mas não é exatamente assim que eles funcionam
Principalmente pelo fato de que eu sou uma desenvolvedora solo e o próprio conceito de microserviços
perde o sentido quando você perde o conceito de equipes responsáveis por partes do dominio
Essas divisões também são pequenas demais para serem serviços, elas são features, talvez tenha 
uns 3 ou 4 serviços aí na pratica
