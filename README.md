# Real time chat - Tecnologias UI, Uai!

Real time chat desenvolvido como exemplo para atividade desenvolvida na 5ª Edição da Escola de Férias PUC Minas. Neste respositório você será capaz de encontrar um real time chat funcional utilizando:
  - HTML/CSS
  - JavaScript
  - Firebase

# Step by Step
## 1. Preparando arquivos
  - Antes de qualquer coisa, definir a estrutura base do nosso arquivo HTML inicial. Para isso, crie um arquivo `index.html` dentro da pasta raiz do nosso projeto e insira a seguinte estrutura. 

        <html>
            <head>
                <!-- Título da tab do navegador -->
                <title>Chat Exercise</title>
                <!-- Para reconhecer pontuações do português -->
                <meta charset="UTF-8">
            </head>
            <body>
            </body>
        <body>

  - Iremos precisar também de um arquivo CSS, onde iremos definir o estilo dos elementos que iremos definir em nosso HTML. Para isso, crie um arquivo `style.css` e deixe-o em branco no momento.
  - Neste momento, qualquer alteração que fizermos no nosso `style.css` não surgirá efeito no `index.html`, uma vez que estes dois não estão ligados. Para isso, adicione a seguinte linha de código no `<head></head>` do seu arquivo `.html` fazendo a conexão dos seus arquivos.
  
        <link rel="stylesheet" type="text/css" href="style.css">

  - Neste arquivo CSS, adicione as seguintes declarações afim de resetar o nosso CSS. De forma que não existam margins ou paddings indesejados e definindo o nosso `background-color` para `#F7F8FC` e nossa `font-family` padrão para Lato.

        body {
            margin: 0;
            padding: 0;
            background-color: #F7F8FC;
            font-family: 'Lato', sans-serif;
        }

        p, h4 {
            width: auto;
            margin: 0;
            padding: 0;
        } 

  - Vamos adicionar também uma fonte personalizada para o nosso site. No site [Google Fonts](https://fonts.google.com) você poderá encontrar algumas bem interessantes e de uso comercial livre. Para este tutorial, vamos usar a fonte Lato. Para adicionar ela no projeto, adicione a seguinte linha no seu `<head></head>`.

        <link href="https://fonts.googleapis.com/css?family=Lato" rel="stylesheet">

  - Neste momento, já temos os arquivos necessários para começar a desenvolver a nossa aplicação, então vamos lá.

## 2. Criando o container principal
  - Nós temos que concordar que é terrível quando entramos em um site e o conteúdo do mesmo já começa a ser exibido logo no canto da tela né? Todos os grandes sites e com boa usabilidade definem um container, centralizado, de cerca de 60% da tela. Para isso, vamos adicionar uma `<div/>` que será este container para nós. Adicione a seguinte linha dentro do seu `<body/>`. É importante ressaltar que como vamos utilizar essa classe de container mais de uma vez, devemos setar-la como uma class.

        <div class="container"></div>

  - De nada serve uma class se não declararmos quais são suas propriedades, então vamos inserir as nossas primeiras linhas do nosso `style.css`.
  - Nós queremos que este nosso container tenha `60%` da largura de seu pai - no caso o `body` - e que seja alinhado ao centro da tela. Para isso, criamos a seguinte declaração CSS.

        .container {
            width: 60%;
            margin-left: auto;
            margin-right: auto;
        }

  - Neste ponto do nosso step by step você já deve ser capaz de visualizar uma página em que todo conteúdo digitado dentro do nosso container estará centralizado no meio da tela, dentro de uma `div` de 60% da tela e utilizando a fonte Lato que definimos.

## 3. Criando o cabeçalho
  - Todo bom website possui um cabeçalho a fim de deixar mais claro para o visitante em qual site ele se encontra no momento. Então vamos criar o nosso.
  - Dentro da nossa div `container` que criamos na seção passada, crie uma nova div com o id `header`. Ela será a responsável por conter o título da nossa página. Para isso, insira a seguinte linha de título dentro da mesma

        <h1>Realtime Chat - Escola de Férias</h1>

  - Para não dizer que não utilizamos o nosso CSS, vamos centralizar o nosso título no centro da página.

        #header {
            text-align: center;
        }

## 4. Criando campos de envio
  - Esta é uma parte importante do nosso projeto, é aonde o nosso cliente poderá digitar qual é o seu nome e qual mensagem deseja enviar. Precisamos deixar ela com um visual bem bacana, então para isso vamos caprichar no CSS.
  - Primeiramente, dentro do nosso `container` e logo após o nosso `header`, crie uma div com o ID `form-send-message`. Como o próprio nome diz, ela será o nosso formulário destinado a enviar mensagem.
  - Dentro desta div, insira 2 `input` com os IDs `input-name` e `input-message` respectivamente.

  - Para deixar com uma boa usabilidade, adicione a propriedade de `placeholder` em ambos inputs.
  - Veja como ficou:
        
        <input id="input-name" placeholder="Insira seu nome"/>
        <input id="input-message" placeholder="Insira sua mensagem"/>

  - De nada adianta esses dois inputs se não tivermos um botão para enviar a mensagem, certo? Então, logo após os inputs, adicione uma tag `button` com ID `send-message-button`

        <button id="send-message-button">ENVIAR</button>

  - Esta aceitável agora. Mas ainda quero mais. Para deixar um pouco mais bonito, vamos substituir este escrito `ENVIAR` por um ícone, o que você acha? Para isso, adicione a seguinte linha de código na última linha do `<body/>` da sua página. Ela será a responsável por importar uma série de ícones da coleção `FontAwesome` para o nosso projeto.

        <script src="https://use.fontawesome.com/6d891047d5.js"></script>

  - Agora só precisamos usa-la. Altere o código de nosso botão para que ele fique da seguinte forma:

        <button id="send-message-button">
            <i class="fa fa-paper-plane" aria-hidden="true"></i>
        </button>

  - Neste momento, temos apenas a estrutura dos nossos campos de envio pronta. Como era de se esperar, tudo está bem feio certo? haha
  - Vamos então começar a trabalhar com o CSS desses componentes que criamos.
  - Em seu `style.css`, crie uma declaração de `#form-send-message` com as seguintes propriedades. Desta forma, esta div passará a ter comportamento de um flexbox. Seguirá a mesma direção do texto de nossa página (`flex-direction`), estará centralizado horizontalmente no centro (`justify-content`) e também estará centralizado verticalmente no centro (`align-items`).

        #form-send-message {
            display: flex;
            flex-direction: row;
            justify-content: center;
            align-items: center;
        }

  - Nós temos dois `input` que terão propriedades similares entre si, então podemos definir estar propriedades que são semelhantes em uma declaração com o seletor `input` e criarmos declarações separadas com os IDs dos mesmos para as atribuições que sejam distintas. Desta forma teremos:

        input {
            padding: 20px;
            border-radius: 15px;
            border: 0;
            box-shadow: 0 5px 19px -2px #d5d5d5;
        }

        #input-name {
            width: auto;
            max-width: 40%;
        }

        #input-message {
            width: 40%;
            margin-left: 15px;
        }

  - Com estas atribuições, nossos dois `input` terão uma margem interna (padding) de `20px`, uma borda arredondada (border-radius) de `15px`, não terão borda (border) e também terão uma sombra projetada (box-shadow).
  - Já o nosso `#input-name` terá a sua largura calculada a partir do seu conteúdo tendo como largura máxima `40%` da largura de seu pai. E o nosso `#input-message` terá a largura fixa de `40%` de seu pai e uma margem de `15px` a esquerda.
  - Por fim, vamos definir o estilo que será aplicado ao nosso botão `#send-message-button`. Para isso, aplique a seguinte declaração.

        #send-message-button {
            border: 0;
            border-radius: 15px;
            background-color: #7643FC;
            color: white;
            padding: 20px;
            box-shadow: 0 5px 19px -2px #d5d5d5;
            margin-left: 15px;
        }
  - O nosso botão não terá borda (border), terá seus cantos arredondados em `15px`(border-radius), seu fundo será da cor `#7643FC`(background-color), seu texto será `white` (color), terá uma margem interna de `20px`(padding), uma sombra projetada (box-shadow) e uma margem na esquerda de `15px`.
  - Pronto! Os nossos campos de envio estão prontos. Vamos agora para os campos aonde nossas mensagens serão exibidas.

## 5. Construindo nosso Chat Container
  - Nesta parte iremos trabalhar em cima da div que será responsável por exibir os balões de mensagem do nosso chat.
  - Para isso, crie uma div com ID `chat-container` em nosso HTML, logo após a `#form-send-message`.
  - Para esta div, declare atribuições de forma que ela ocupe `100%` da largura de seu pai, tenha uma altura relacionada com a quantidade de conteúdo que ela possui e que tenha uma margem superior de 30px. Desta forma, iremos obter o seguinte estilo.
  
        #chat-container {
            width: 100%;
            height: auto;
            margin-top: 30px;
        }

## 6. Criando o nosso balão de mensagem
  - O balão de mensagem será o container aonde será exibido quem enviou a mensagem e o conteúdo da mesma. A ideia é semelhante a usada em aplicativos famosos como Whatsapp e Telegram. Caso você tenha dúvida, consulte eles.
  - Dentro da div `#chat-container`, crie uma outra div com a class `row`.
  - Para estas classes, vamos usar a seguinte atribuição; que será responsável por determinar que não exista nenhum outro balão do lado do balão desta mensagem, uma vez que sua largura esta setada para `100%` e estamos ignorando qualquer atributo de `float` com o `clear`.

        .row {
            width: 100%;
            height: auto;
            clear: both;
        }

  - Agora precisamos criar a div que será responsável por conter o balão de menssagem em si. Para isso, crie uma div com as classes `message-content float-right` caso você queira criar um balão a direita da tela ou troque para `message-content float-left` caso queira uma balão a esquerda.
  - Falar sobre as atribuições agora


### Todos

 - Write MOAR Tests
 - Add Night Mode

License
----

MIT


**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)


   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
