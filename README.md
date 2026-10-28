# CineTag

O CineTag é uma aplicação web feita com React para explorar vídeos, abrir um player e organizar vídeos favoritos. A navegação entre as telas é feita com React Router, e a lista de vídeos é carregada de uma API externa.

## Tecnologias e assuntos estudados

O projeto foi desenvolvido durante um curso e reúne os seguintes assuntos:

- **React**: criação da interface com componentes.
- **React Router DOM**: navegação entre as páginas sem recarregar a aplicação.
- **CSS Modules**: estilos isolados por componente e página.
- **Context API**: compartilhamento do estado dos favoritos entre componentes.
- **Hooks**: gerenciamento de estado e efeitos com hooks como `useState`, `useEffect` e `useContext`.
- **HTML, CSS e JavaScript**: tecnologias fundamentais usadas na construção da aplicação.

## Pré-requisitos

- [Node.js](https://nodejs.org/) e npm instalados.
- Acesso à internet para carregar os vídeos da API e as fontes externas.

## Como executar o projeto

1. Abra um terminal na pasta do projeto.
2. Instale as dependências:

   ```bash
   npm install
   ```

3. Inicie o servidor de desenvolvimento:

   ```bash
   npm start
   ```

4. Acesse [http://localhost:3000](http://localhost:3000) no navegador.

O servidor de desenvolvimento atualiza a página automaticamente quando os arquivos são alterados. Para encerrá-lo, use `Ctrl + C` no terminal.

## Como usar

1. **Home (`/`)**: exibe os vídeos recebidos pela API.
2. **Abrir um vídeo**: selecione um card para acessar a rota do vídeo e visualizar o player.
3. **Favoritos (`/favoritos`)**: reúne os vídeos marcados como favoritos durante a navegação.

Os favoritos são mantidos em memória pelo contexto React; não há persistência configurada, então a lista é reiniciada ao recarregar a página.

## Scripts disponíveis

| Comando | Descrição |
| --- | --- |
| `npm start` | Inicia a aplicação em modo de desenvolvimento. |
| `npm test` | Executa os testes configurados pelo Create React App. |
| `npm run build` | Gera a versão de produção na pasta `build/`. |

## Dados dos vídeos

A aplicação busca a lista de vídeos e os dados de cada vídeo na API:

`https://my-json-server.typicode.com/monicahillman/cinetag-api/videos`

Portanto, o carregamento dos vídeos depende de a API estar acessível. O projeto não configura um servidor de API local.

## Organização do projeto

```text
public/                 Arquivos públicos e HTML inicial
  imagens/              Banners e ícones usados pela aplicação
src/
  components/           Componentes reutilizáveis, como cabeçalho, cards e banners
  contextos/             Contexto React para o estado dos favoritos
  pages/                 Telas: início, favoritos, player e página não encontrada
  json/                  Pasta destinada a arquivos JSON
  routes.js              Configuração das rotas da aplicação
  index.js               Ponto de entrada do React
  index.css              Estilos globais
```

### Fluxo da aplicação

1. `src/index.js` monta a aplicação React no elemento `root` do HTML.
2. `src/routes.js` configura as rotas e envolve as páginas com a estrutura base.
3. `src/pages/PaginaBase` renderiza o cabeçalho, o conteúdo da rota e o rodapé; também disponibiliza o contexto de favoritos.
4. A página inicial busca os vídeos na API e apresenta cada item como um card.
5. A página do player usa o identificador da rota para solicitar os dados do vídeo correspondente.
