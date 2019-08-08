### Estudos sobre compartilhamento de components React

Trabalhando em um projeto, houve a necessidade de compartilhamento de componentes de uma aplicação React com outra Aplicação.

Basicamente temos uma Aplicação base, e precisávamos compartilhar todos os componentes dessa aplicação com outra que iriamos desenvolver
sem precisar reescrever todos os componentes novamente.

Pesquisando muito e com ajuda de alguns amigos, conheci o <a href="https://bit.dev" target="_blank">Bit.Dev</a> onde voce desenvolve seus componentes normalmente, e de uma forma muito simples o Bit.dev isola seus componentes e as suas respectivas dependência e deixa aquele componente totalmente isolado dos demais podendo utiliza-lo em outras aplicações sem gerar nenhum conflito.


Este repositório é da aplicação de exemplo, e <a href="https://bit.dev/marcelxsilva/blog-simple" target="_blank">aqui está os componentes desenvolvidos</a> prontos para ser baixados e testados na sua aplicação:

Está aplicação é um exemplo bem simples de um blog e como se aplicar o conceito de shared components in react

<a href="https://marcelxsilva-blog-simple.herokuapp.com" target="_blank">Demo preview</a>

## Como tudo acontece
Antes de tudo, crie sua conta no <a href="https://bit.dev" target="_blank">Bit.Dev</a> e crie uma collection.

Seguindo a <a href="https://docs.bit.dev" target="_blank">documentação</a>  somos orientados a:

Instalar Bit.dev

<code>
$ npm install bit-bin -g
</code>

Criar um diretório para o seu projeto e iniciar um bit Workspace:


<code>
$ cd project-directory
$ bit init
</code>

Em seguida, crie uma aplicação react como sempre fez:

<code>
$ create-react-app demo
</code>

Seguindo alguns padroes de organização de código, crie a pasta de components detro de src e comece a desenvolver seus componentes normalmente:

<pre>
└── src
    └── components
        ├── Button
        │   └── index.js
        └── index.js

</pre>
Costumo deixar dessa forma, criei um componente chamado Button com seu arquivo index.js e dentro da pasta de components junto com as demais pastas coloco outro arquivo index.js que ira exportar todos os componentes de uma só vez, pois quando eu for importar dentro de outra aplicação apenas faço assim:

<code>
import { Button } from '@bit/marcelxsilva.< nome da collection >.components';
</code>

Arquivo index.js da pasta components:

<pre>
export * from './Button'
</pre>

Após criar todos os seus componentes, digite no terminal:

<code>
$ bit add src/components
</code>

Semelhante ao git, ele ira carregar todos os componentes dentro daquele diretório.

Em Seguida, informe qual vai ser o compilador daqueles componentes:

<code>
    $ bit import bit.envs/compilers/react --compiler
</code>

 <a href="https://bit.dev/bit/envs" target="_blank">Lista dos compiladores suportados</a>


Em seguida:

<code>
    $ bit build
</code>

Informe qual a versão dos seus componentes:

<code>
bit tag --all 1.0.0
</code>


Agora faça login no Bit pelo terminal:

<code>
$ bit login
</code>

Ele pedirá permissão para abrir o navegador e realizar o login

E agora é só exportar seus componentes, inserindo seu nome de usario e a collection que criou.

<code>
$ bit export user-name.collection-name
</code>

Agora em outras Aplicações React, apenas instale sua collection e as importe para o projeto:

<code>
$ yarn add user-name.collection-name.componentes

import { Button } from  user-name.collection-name.componentes

</code>

Tudo certo, qualquer duvída <a href="https://docs.bit.dev" target="_blank"> consulte a documentação </a> ou pode <a href="mailto:maarcelomonteiro@gmail.com"> falar comigo </a> mesmo.