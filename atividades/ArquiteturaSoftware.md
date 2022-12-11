**UNIVERSIDADE FEDERAL DO CEARÁ – UFC SOBRAL ENGENHARIA DE SOFTWARE – PROF. FISCHER![](Aspose.Words.aadf69e8-8c9b-437e-907b-364dd88fb173.001.png)**

**Parte 1 - Exercícios de Fixação**

1. Dada a sua complexidade, sistemas de bancos de dados são componentes relevantes na arquitetura de qualquer tipo de sistema. Verdadeiro ou falso? Justifique a sua resposta.

R: Falso, pois dependendo do tipo de sistema talvez não seja estritamente essencial ter um banco de dados. Por exemplo, em um sistema cuja responsabilidade seja apenas obter mensagens ou dados de um serviço e enviar a outro, sem a necessidade de guardar estes dados transitados.

2. Descreva três vantagens de arquiteturas MVC.

R: Divisão de responsabilidades entre diferentes componentes do software. Facilidade no momento de “debuggar”, descobrir problemas e resolvê-los. Facilidade de implementar novas funcionalidades em modificar outras partes do sistema.

3. Qual a diferença entre classes Controladoras em uma Arquitetura MVC tradicional e classes Controladoras de um sistema Web implementado usando um framework MVC como Ruby on Rails?

R: Enquanto que em um padrão MVC tradicional para aplicações desktop tem-se um controlador identificando as interações do usuário por meio de mouse e teclado e enviando informações ao modelo, no MVC web tem-se uma classe controladora

mapeando as interações do usuário com a própria página web.

4. Descreva resumidamente quatro vantagens de microsserviços.

R: Escalabilidade, tornando mais fácil derrubar, subir ou realizar manutenção em processos (conjuntos de módulos) do serviço. Facilidade de lançar uma release de alguma funcionalidade sem precisar modificar outras funcionalidades. Tem-se separação de responsabilidades do sistema. Facilidade em atuar em manutenções de processos falhos.

5. Por que microsserviços não são uma bala de prata? Isto é, descreva pelo menos três desvantagens do uso de microsserviços.

R: Dependendo da forma que os serviços compartilham dados (bancos de dados), as classes podem ter um alto acoplamento. Não deve ser utilizada quando a latência for um fator crucial para o sistema.

6. Explique a relação entre a Lei de Conway e os microsserviços.

R: Alei de Conway diz que a arquitetura/estrutura de um software possui relação com

a estrutura organizacional de uma empresa. Se uma companhia possui uma comunicação ruim e uma estrutura de times generalista, é muito provável que o software desenvolvido pela empresa seja repleto de burocracias e venha a ser um grande monolito. No entanto, se a empresa divide os times pela necessidade de negócio, em times pequenos, auto organizáveis e especialistas, e ainda se esses times conseguem conversar de forma eficiente entre si, então é muito provável que o software como micro serviço venha a ser desenvolvido com sucesso.

7. Explique o que significa desacoplamento no espaço e desacoplamento no tempo. Por que arquiteturas baseadas em filas de mensagens e arquiteturas Publish/Subscribe oferecem essas formas de desacoplamento?

R: Por meio do desacoplamento de espaço, o cliente não precisa conhecer os detalhes do servidor no qual os dados são consumidos, bastando ter um sistema intermediário para que essa troca de dados ocorra. Desacoplamento no tempo

significa que o cliente e o servidor não precisam estar simultaneamente no ar, podendo algum dos dois estar desligados, e os dados trocados pelas duas entidades nesse período serão armazenados até que o outro serviço volte a funcionar. Estes conceitos podem ser definidos utilizando a arquitetura de mensagens, pois nela um sistema intermediário cuida da troca de mensagens entre cliente e servidor. Da mesma forma ocorre no padrão publish/subscribe, onde um serviço está entre o(s) cliente(s) e o(s) servidor(es) cuidando da publicação, obtenção e notificação de eventos.

8. Quando uma empresa deve considerar o uso de uma arquitetura baseada em filas de mensagens ou uma arquitetura publish/subscribe?

R: Dependendo da quantidade de consumidores de uma aplicação de banco de dados. Sendo esta quantidade alta, é interessante utilizar um padrão publish/subscribe. Enquanto não houver muitos consumidores, será melhor utilizar uma arquitetura de mensageria.

9. Explique o objetivo do conceito de tópicos em uma arquitetura

publish/subscribe.

R: Os tópicos nada mais são do que uma categoria dos eventos recebidos pelo serviço publish/subscribe. Assim, os consumidores não necessitam assinar todos os eventos que chegarem ao serviço intermediário, mas sim apenas aqueles que forem do seu tópico de interesse.

10. (POSCOMP, 2019, adaptado) Marque V ou F.

( F ) O padrão MVC é uma adaptação do padrão arquitetural Camadas. A Camada Visão lida com a apresentação e a manipulação da interface, a Camada Modelo organiza os objetos específicos da aplicação, e a Camada Controle posiciona-se entre estas duas com as regras do negócio.

( V ) O padrão Broker é voltado a problemas de ambientes distribuídos. Sugere uma arquitetura na qual um componente (broker) estabelece uma mediação que permite um desacoplamento entre clientes e servidores.

( V ) Mesmo que um dado padrão arquitetural ofereça uma solução para o problema sendo resolvido, nem sempre ele é adequado. Fatores como contexto e o sistema de forças que afeta a solução fazem também parte do processo de avaliação e da escolha de padrões adequados.

**Parte 2 - Atividades práticas**

1) Exemplo (didático) de um sistema MVC Web:

https://replit.com/@engsoftmoderna/ExemploArquiteturaMVC Navegue no link **Show files** para visualizar o fonte do projeto.

Indique quais arquivos devem ser alterados para que o sistema de exemplo possibilite a consulta pelo “isbn text” do livro.

R:

a) O arquivo “ControladorPesquisaLivros” dentro da pasta “Controladores”, adicionando um código similar à pesquisa de autor, mas agora utilizando “isbn” na query de parâmetros. Isso pensando que seria possível pesquisar unicamente pelo isbn, caso fosse possível pesquisar por isbn ou autor, talvez se tornasse necessário utilizar um comando de tratamento de exceção.

b) No arquivo "ServicoPesquisaLivros" dentro da pasta "Modelos", deveria haver um método chamado ``pesquisaPorIsbn``, recebendo como argumento uma variável chamada **isbn** como string. Ademais, depois de criar a query para o banco, o caractere '?' deveria ser substituído pela variável isbn utilizando a função **setStrin**:

```Java
String query = "select * from livros where autor = ?";
...
stmt.setString(1, isbn);
```

2) Roteiro prático sobre microsserviços https://github.com/aserg-ufmg/micro-livraria

2.1**Tarefa Prática #1: Implementando uma Nova Operação**

2.2**Tarefa Prática #2: Criando um Container Docker**

3) Roteiro prático sobre Publish/Subscribe https://github.com/aserg-ufmg/pub-sub-store
1. **Passo 1: Instalando, Executando e Inicializando**
   1. **RabbitMQ**
1. **Passo 2: Subindo os Serviços**
1. **Passo 3: Colocando a Mão na Massa**

**Atenção à entrega: Poste os arquivos que você trabalhou nestas atividades na sua conta do GitHub e coloque o link no google Classroom do seu projeto no GitHub.**
