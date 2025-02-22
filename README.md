# VTEX-IO - Leodário Júnior
### Baseando no store theme
[store theme](https://storetheme.vtex.com/)

### Usando a versão nodejs 14
Usando o nvm para versionar o nodejs

### Clonar o git do store theme
[Git Sotre Theme](https://github.com/vtex-apps/store-theme)

### Instalar CLI VTEX
- Windows: 
```
yarn global add vtex
```

### Ver a versão da VTEX
```
vtex -v
```
### Logar na minha conta VTEX
- vtex login <nome-da-loja> (exemplo: https://www.nome-da-loja.myvtex.com/admin)

- Deverá aparecer uma mensagem no navegador como essa abaixo:

Você já pode fechar essa janela.

You may now close this window.

Ahora puedes cerrar esta ventana.

### Como que sempre você irá utilizar para iniciar o trabalho
- O comando abaixo indica qual loja você está trabalhando
```
vtex whoami
```
### Para obter ajuda de comandos da VTEX
```
vtex help
```

### Para saber a lista de opções que a VTEX possui (ex: dependências)
```
vtex ls
```

## 2 - Instalando Depedências VTEX
### Instalando um app VTEX. Exemplo:
- vtex install <nome-do-app> (exemplo: vtex install store-theme)
- vtex.search-graphql está atualmente na versão 0.65.0
- para instalar a versão mais recente
```
vtex install vtex.search-graphql@0.x
```

### Para desinstalar um app VTEX da loja
- vtex uninstall <nome-do-app> (exemplo: vtex uninstall store-theme)
```
vtex uninstall vtex.search-graphql@0.x
```
### Verificando se tem algum app desatualizado e atualizar
```
vtex update
```
### Comandos necessários para instalar. O admin possui a funcionalidade de editar o Sotrefront e seus componentes na master:
- vtex install vtex.admin@4.x (Instala a versão do admin compatível com storefront)
- vtex install vtex.admin-pages@4.x (Adiciona a aba de configurações de "Páginas" no CMS)
- vtex install vtex.admin-apps@4.x (Adiciona a página de apps correta no admin)
- vtex install vtex.colossus-legacy-proxy@2.x (Corrige redirecionamentos do site)
- vtex install vtex.rewriter@1.x --force (Corrige redirecionamentos do site)


### Comando que faz a loja VTEX CMS (legado) virar VTEX IO (muito cuidado ao usar este comando)
- vtex install vtex.store@2.x--force (não faça na master, faça primeiro no workspace)

### Configurando manifest.json (neste caso estou usando o app tema store-theme)
- "vendor": "nome-da-loja",

### Para listar comandos do workspace
- vtex workspace ls

### Criando um workspace
- vtex use <nome-do-workspace>
- vtex use leodario (exemplo)

### Para voltar para a master
- vtex use master

### Para saber qual workspace que estou 
- vtex whoami

### Listar comandos do VTEX workspace
- vtex workspace

### Listar quais workspace possui criado
- vtex workspace ls

### Para deletar um workspace
- vtex workspace delete <nome-do-workspace>

### Desistanlando um tema no workspace
- vtex uninstall <nome-do-app> (exemplo: vtex uninstall store-theme)
- vtex uninstall codebluepartnerbr.padrao@1.x  

### Atualizando apps
- vtex install <nome do app>
- vtex install vtex.store@2.x --force



### Enviando os arquivos para o git
- git status
- git add .
- git commit -m "descrição do commit"
- vtex release patch stable
- vtex deploy -f

### Linkando VTEX - comando que você usará sempre
```
vtex link
```

### Pode ocorrer alguns erros
- primeiro atualize todos os apps verificando digitando vtex ls
- caso econtre algum tema desatualizado utilize o comando vtex install <nome do app>
- após atualizar tudo e conseguir usar o camdando vtex link sem erro, pode ser que dê erro de página. Para corrigir vá no painel administrativo, vá em Storefront > Páginas > Home e procure o endereço do workspace criando. Exemplo https://leodario--codebluepartnerbr.myvtex.com

### Acessando workpace no navegador via comando no terminal
- vtex browser

### O Intelligent Search da vtex tem que estar instalado
- [Intelligent Search](https://developers.vtex.com/docs/apps/vtex.search)
- Digite vtex ls para verificar se possui (vtex.admin-search@1.x e vtex.search-resolver@1.x)
- No manifest.json é preciso ter também
```
 "dependencies": {
    "vtex.search": "2.x"
  }
```
### Extesão .jsonc
- A extensão .jsonc é usada pela VTEX para definir a estrutura e a configuração de blocos em lojas online. O .jsonc é uma variação do formato JSON, mas com suporte a comentários, o que facilita a documentação e a organização do código.

- Na prática, os desenvolvedores da VTEX utilizam arquivos .jsonc para configurar e personalizar o layout e os componentes das páginas de e-commerce. Por exemplo, você pode encontrar arquivos .jsonc na pasta /store/blocks do seu tema, que determinam como os blocos são organizados na página inicial
### Página de produto
- É comum a primeira vez você não conseguir abrir a página de produto, e até mesmo dar erro. É necessário abrir um chamado no suporte da vtex [help.vtex.com](https://help.vtex.com/). Pedindo ao suporte a liberação para a loja Edition para edição.
- Para verificar se a loja Edition Apps está ativa, você digita vtex ls e aparecerá conforme o exemplo abaixo:
<img src="./doc-imagens/app-edition.PNG" style="display: block; width: 90%; margin:20px 0;">
_______________________________________________________________
## Fontes, styles assets e container
- [Figma de exemplo layout](https://www.figma.com/design/IRGyFQ9W9alhxcv5bAGz3n/Summer-(Copy)?node-id=62-4&t=K3Sxx47U7MpySh4H-1)
- [Documentação Vtex Layout](https://developers.vtex.com/docs/apps/vtex.slider-layout)
### Baixando fontes e dicas
- No layout exemplo vou utilizar a fonte [amiko](https://fonts.google.com/specimen/Amiko?query=amiko)
- Dica a fonte com a extensão .ttf não é a mais indicada para projetos web, o mais indicado é com a extensão .woff2. Caso você tenha baixado a extensão .ttf, você pode converter a extensão para .woff2 através deste [link Converter](https://cloudconvert.com/ttf-to-woff2) 
<img src="./doc-imagens/fonte-amiko.PNG" style="display:block; width:90%; margin:20px 0;">

### Baixando assets vtex io
- Por padrão o assets não é criado, você precisa criar manualmente
- [Documentação Assets Vtex IO](https://developers.vtex.com/docs/guides/vtex-io-documentation-using-the-assets-builder)
- No manifest.json você insere o código abaixo:
```
"builders": {
  "assets": "0.x"
},
- Crie uma pasta assets na raiz do projeto.
```
<img src="./doc-imagens/vtex-io-documentation-using-the-assets-builder-0.png" style="display:block; margin:20px 0;">

- Para chamar as fontes [Documentação](https://developers.vtex.com/docs/guides/vtex-io-documentation-customizing-your-stores-typography)
- Em <u>styles/configs</u> pasta, crie um novo arquivo chamado <u>font-faces.css</u>.
- Em <u>styles/configs/style.json</u> é onde você padroniza as cores, textos do projeto
- <b>*Dica</b>: pode acontecer se você estover linkado com o workspace, as atualizações podem não sutir efeito. Utilize o comando baixo para deslinkar, e depois linka novamente.
```
vtex unlink -a
// Posteriormente linka novamente
vtex link -c
```

## Texto e Markdown
- A vtex utiliza em alguns casos o markdow para formatar texto. Veja [Link guia markdonw](https://www.markdownguide.org/cheat-sheet/). Você utilizará muito no seu dia a dia.
- Por padrão em store > blocks > home > home.jsonc
- Exemplo o "rich-text#shelf-title"
- <img src="./doc-imagens/rich-text.PNG" style="display:block, width:90%; margin:20px 0;">
- Depois é chamado com sua formatação
- <img src="./doc-imagens/rich-text-block.PNG" style="display:block, width:90%; margin:20px 0;">
- blockClass: é uma classe global, ele dará uma classe css única
- text: para inserir os textos
- Componentes de links é mais indicado usar o próprio da vtex [Veja a documentação](https://developers.vtex.com/docs/apps/vtex.store-link)
### Dica
- Instale a extesnão VTEX IO Intellisense. Ela sugere o autocomplete no seu código vtex

## Imagens
```
{
  "store.home":{
    "blocks": [
      "image#imagem-teste",
    ]    
  }
}
```
- Para declarar para chamá-lo:
```
"image"#imagem-teste":{
  "props":{
    "alt": "Imagem de exemplo",
    "src": "assets/imagem-vtex.png"
  }
},
```
- [lista de props para imagem VTEX IO](https://developers.vtex.com/docs/apps/vtex.store-components/image)

- ### Image list 
- Usado para banners principalmente
- [Documentação](https://developers.vtex.com/docs/apps/vtex.store-components/image-list)
- Exemplo:
```
{
  "store.home": {
    "blocks": [
      "list-context.image-list#demo",
      
    ]
  },
}

"list-context.image-list#demo": {
    "children": ["slider-layout#demo-images"],
    "props": {
      "height": 570,
      "preload": true,
      "images": [
        {
          "image": "https://storecomponents.vteximg.com.br/arquivos/Class&Style-desktop.png",
          "mobileImage": "https://storecomponents.vteximg.com.br/arquivos/Class&Style-mobile.png"
        },
        {
          "image": "https://storecomponents.vteximg.com.br/arquivos/banner-decoration.png",
          "mobileImage": "https://storecomponents.vteximg.com.br/arquivos/banner-decoration-mobile.png"
        }
      ]
    }
  },
```
### Imagem infocard
```
{
  "store.home": {
    "blocks": [      
      "info-card#home",     
    ]
  },
}

"info-card#home": {
    "props": {
      "id": "info-card-home",
      "isFullModeStyle": false,
      "textPosition": "left",
      "imageUrl": "https://storecomponents.vteximg.com.br/arquivos/banner-infocard2.png",
      "headline": "Clearance Sale",
      "callToActionText": "DISCOVER",
      "callToActionUrl": "/sale/d",
      "blockClass": "info-card-home",
      "textAlignment": "center"
    }
  },
```
<img src="./doc-imagens/inforcard.PNG" style="display:block; width:100%; margin:20px 0;">
- [Link da documentação Info Card](https://developers.vtex.com/docs/apps/vtex.store-components/infocard)

## Site editor e title
- No admin vtex você vai no menu Sotrefront > Site Editor
- É uma ferramenta de gerenciamento de conteúdo (CMS) projetada para facilitar a personalização da vitrine de lojas desenvolvidas com o Store Framework da VTEX1. Ele permite que usuários não técnicos gerenciem e modifiquem o conteúdo da loja de maneira intuitiva, sem a necessidade de alterar o código.

### Com o Site Editor, você pode:

- <b>Editar blocos de conteúdo:</b> Modificar textos, imagens e outros elementos diretamente na vitrine.
- <b>Gerenciar componentes: </b>Alterar propriedades de componentes, como prateleiras de produtos e banners.
- <b>Visualizar mudanças em tempo real:</b> As alterações feitas são refletidas imediatamente na loja.

### Boa práticas no Site Editor
- Os nome dos Blocos é importante ter nomes fáceis para o cliente entender a nomeclatura
<img src="./doc-imagens/site-editor-bloco.PNG" style="display:block; width: 50%; margin:20px 0;">
- Para isso você tem um atributo global no bloco de código que você pode dar nome para qualquer atributo. Exemplo:
```
"title": "Banner Principal"
```
<img src="./doc-imagens/atributo-title.PNG" style="display:block; width: 80%; margin:5px 0;">
<img src="./doc-imagens/bloco-banner-principal.PNG" style="display:block; width: 50% margin:20px 0;">

## Tabless com Flex - vtex io
- Vou pegar o arquivo deals.json como exemplo. Ele geralmente fica abaixo do banner principal.

<img src="./doc-imagens/deals.PNG" style="display:block; width: 100%; margin:20px 0;">

- Exemplo de deals.json
```
{
  "flex-layout.row#deals": {
    "children": [
      "flex-layout.col#deals1",
      "flex-layout.col#deals2",
      "flex-layout.col#deals3",
      "flex-layout.col#deals4"
    ],
    "props": {
      "blockClass": "deals"
    }
  },
  "flex-layout.col#deals1": {
    "children": [
      "image#deal1",
      "rich-text#deal1"
    ]
  },
  "image#deal1": {
    "props": {
      "src": "https://storecomponents.vteximg.com.br/arquivos/box.png",
      "maxHeight": "24px"
    }
  }
}
```
- [Lisnk da documentação VTEX Flex Layout](https://developers.vtex.com/docs/apps/vtex.flex-layout)
- Geralmente no dia a dia acabamos usando o CSS. Na prática o que acabamos usando mais é o <u>colSizing</u>, portualmente o <u>verticalAlign</u>

## Estilos
- Para descobrir qual nome do arquivo que está estilizando determiado elemento, uma das maneiras é inspensionando o elemento. Exemlo o deals
<img src="./doc-imagens/vtex-flex-layout.PNG" style="display:block; width: 80%; margin:20px 0;">
- No exemplo acima o arquivo é vtex.flex.layout.css
- Quando quero estilizar um elemento em específico, porém a classe .css, está em diversos lugares, você locarliza o pai. Exemplo: pai(.flexRow--deals), filho(.vtex-rich-text-0-x-paragraph). Ficando assim:
```
.flexRow--deals :global(.vtex-rich-text-0-x-paragraph){
  background: #900;
}
```
- Se um determinado elemento não tiver um arquivo específico, exemplo: .vtex-button devemos colocar uma ação global também. Você localiza o pai dele, exemplo: .vtex-product-sumary-element
```
.vtex-product-sumary-element :global(.vtex-button ){
  background: #ccc;
}
```
## Configurações Gerais e Favicon
- Para configurar o favicon <u>Configurações Gerais da Loja > Loja</u> e em ADICIONAR
<img src="./doc-imagens/configurar-favicon.PNG" style="display:block; width: 70%; margin:20px 0;">
- Para subir imagem do favicon na vtex no final da url você coloca /a
- Exemplo: https://leodario--codebluepartnerbr.myvtex.com/admin/a

### __fold__ - Carregar o site mais rápido na parte visível da home
- Para configurar o carregamento mais rápido onde o usuário visualiza o site ao carregar a home, você ativará a emgrenagem __fod__ dentro de loja conforme o print abaixo:
<img src="./doc-imagens/fold-loja.PNG" style="display:block; width: 100%; margin:20px 0;">
- E no arquivo home.jsonc para configurar a dobra
<img src="./doc-imagens/fold-json.PNG" style="display:block; width: 80%; margin:20px 0;">

### Ícones
- [Documentação](https://developers.vtex.com/docs/apps/vtex.store-icons)
- [Customização](https://developers.vtex.com/docs/guides/vtex-io-documentation-customizing-your-stores-icons)
- No tema da sua loja, crie uma nova pasta com o nome iconpacks dentro da styles pasta.
- Dentro da iconpacks pasta, crie um arquivo chamado iconpack.svg.
- Copie o conteúdo do arquivo iconpack.svg e cole-o no seu iconpack.svgarquivo.
<img src="./doc-imagens/pasta-iconpaks.PNG" style="display:block; width: 50%; margin:20px 0;">

### Mudando um icone
- Por exemplo, irei mudar o icon do cart conforme o print abaixo:
<img src="./doc-imagens/cart.PNG" style="display:block; margin:20px 0;">
- Inspenciono o elemento para descobrir o id do icon .svg
- No print abaixo é hpa-cart

<img src="./doc-imagens/hpa-cart.PNG" style="display:block; margin:20px 0;">

- O padrão do código svg. Dentro de <symbol></symbol> que você cola o arquivo srvg que baixamos do figma por exemplo

```
<​svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" >  

    <symbol> 

    </symbol>

</svg>
```
- Inserindo o id do arquivo inspensionado 

```
<svg  xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <symbol>
    <g id="hpa-cart">

    </g>
  </symbol>
</svg>

```
- No arquivo baixado do figma você copia a partir da tag <path>

```
<svg  xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <symbol>
    <!-- Ícone de carrinho -->
    <g id="hpa-cart">
      <path d="M5.44303 1.58325L2.98688 4.74992V15.8333C2.98688 16.2532 3.15939 16.6559 3.46647 16.9528C3.77355 17.2498 4.19004 17.4166 4.62431 17.4166H16.0864C16.5206 17.4166 16.9371 17.2498 17.2442 16.9528C17.5513 16.6559 17.7238 16.2532 17.7238 15.8333V4.74992L15.2676 1.58325H5.44303Z" stroke="#43483B" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M2.98688 4.75H17.7238" stroke="#43483B" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M13.6302 7.9165C13.6302 8.75636 13.2852 9.56181 12.671 10.1557C12.0569 10.7495 11.2239 11.0832 10.3553 11.0832C9.48679 11.0832 8.65382 10.7495 8.03966 10.1557C7.4255 9.56181 7.08047 8.75636 7.08047 7.9165" stroke="#43483B" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
    </g>
  </symbol>
</svg>

```
## Bloco de Login
- Quando um bloco de login nunca for declarado, você pode seguir esta documentação: [Vtex login](https://developers.vtex.com/docs/apps/vtex.login)

-----


