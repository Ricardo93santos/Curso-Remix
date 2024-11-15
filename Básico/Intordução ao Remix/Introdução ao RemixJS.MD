# Introdução ao RemixJS

## O que é RemixJS?
RemixJS é um framework para construção de aplicações web baseadas em React que se destaca pela sua capacidade de renderização no servidor (Server-Side Rendering, SSR) e na otimização da performance. Ele facilita o desenvolvimento de aplicações dinâmicas e interativas, garantindo que o carregamento inicial seja rápido e eficiente.

**Principais Benefícios do RemixJS:**
- **Renderização Isomórfica:** Permite que a aplicação seja renderizada tanto no servidor quanto no cliente, melhorando a performance inicial e SEO.
- **Roteamento Aninhado:** Simplifica a criação de rotas complexas e layouts reutilizáveis.
- **Dados Primeiro:** Abordagem centrada em dados, priorizando o carregamento e manipulação de dados no servidor.
- **Gestão de Estado Simplificada:** Integração facilitada com Context API e outros gerenciadores de estado.

<br>

# Instalação e Configuração do Ambiente

## Pré-requisitos
- **Node.js:** Certifique-se de ter o Node.js instalado. Você pode verificar isso executando `node -v` no terminal.
- **npm (Node Package Manager):** Geralmente vem com o Node.js. Verifique com `npm -v`.

## Criando um Projeto RemixJS
Use o comando abaixo para criar um novo projeto RemixJS:
```bash
npx create-remix@latest my-remix-app
cd my-remix-app
npm install
npm run dev
```
- `npx create-remix@latest:` Cria um novo projeto RemixJS.
- `cd my-remix-app:` Navega até a pasta do projeto.
- `npm install:` Instala todas as dependências necessárias.
- `npm run dev:` Inicia o servidor de desenvolvimento.

<br>

# Estrutura Básica do Projeto RemixJS

Quando você cria um novo projeto RemixJS, ele vem com uma estrutura de diretórios que facilita a organização do código. Aqui estão os diretórios e arquivos mais importantes:

## Estrutura de Diretórios
- **`app/`**: Diretório principal onde você vai desenvolver a maior parte da aplicação.
  - **`routes/`**: Todos os arquivos e pastas aqui representam rotas. Cada arquivo `.jsx` ou `.tsx` define uma rota. Por exemplo, `app/routes/index.jsx` corresponde à rota raiz (`/`).
  - **`components/`**: Componentes React reutilizáveis. Se você tiver um botão ou uma barra de navegação que será usado em várias partes da aplicação, você os colocaria aqui.
  - **`styles/`**: Arquivos de estilo (CSS, SCSS) para a aplicação.
  - **`entry.client.tsx` e `entry.server.tsx`**: Pontos de entrada para o cliente e servidor, respectivamente.

- **`public/`**: Arquivos estáticos como imagens, ícones e fontes. Tudo neste diretório é servido diretamente pelo servidor.

- **`remix.config.js`**: Arquivo de configuração principal do RemixJS. Aqui você define as rotas, configuração de loaders, paths e outros parâmetros de configuração.

- **`package.json`**: Lista as dependências do projeto, scripts de build, e informações gerais do projeto.

- **`node_modules/`**: Diretório onde estão instaladas todas as dependências do projeto. Este diretório é gerado automaticamente após rodar `npm install`.

<br>

# Primeira Aplicação: "Hello World"

## Passo 1: Criando a Estrutura Inicial
1. **Crie um novo projeto RemixJS:**
   - Abra seu terminal e execute o seguinte comando para criar um novo projeto RemixJS:
     ```bash
     npx create-remix@latest my-remix-app
     cd my-remix-app
     npm install
     npm run dev
     ```
   - Isso criará uma nova pasta chamada `my-remix-app`, instalará todas as dependências necessárias e iniciará o servidor de desenvolvimento.

2. **Estrutura do Projeto:**
   - Após executar os comandos acima, você terá a seguinte estrutura de diretórios:
     ```
     my-remix-app/
     ├── app/
     │   ├── routes/
     │   │   └── index.jsx
     │   ├── components/
     │   ├── styles/
     │   ├── entry.client.tsx
     │   └── entry.server.tsx
     ├── public/
     ├── remix.config.js
     ├── package.json
     └── node_modules/
     ```

## Passo 2: Criando a Rota Principal
1. **Criar o arquivo da rota principal:**
   - No diretório `app/routes`, crie um arquivo chamado `index.jsx`:
     ```jsx
     export default function Index() {
       return (
         <div>
           <h1>Hello, Remix!</h1>
           <p>Bem-vindo à sua primeira aplicação RemixJS.</p>
         </div>
       );
     }
     ```
   - Este arquivo define a rota raiz (`/`). O componente `Index` é um componente React que renderiza uma mensagem "Hello, Remix!".

## Passo 3: Adicionando Estilo
1. **Criar um arquivo de estilos:**
   - No diretório `app/styles`, crie um arquivo chamado `global.css`:
     ```css
     body {
       font-family: Arial, sans-serif;
       margin: 0;
       padding: 0;
       display: flex;
       justify-content: center;
       align-items: center;
       height: 100vh;
       background-color: #f0f0f0;
     }

     h1 {
       color: #333;
     }
     ```

2. **Importar os estilos:**
   - No arquivo `app/root.jsx`, importe o arquivo de estilos:
     ```jsx
     import styles from "./styles/global.css";

     export const links = () => [
       { rel: "stylesheet", href: styles }
     ];

     export default function App() {
       return (
         <html>
           <head>
             <meta charSet="utf-8" />
             <title>My Remix App</title>
           </head>
           <body>
             <Outlet />
           </body>
         </html>
       );
     }
     ```
   - O componente `App` configura o HTML básico da aplicação e o `Outlet` é onde as rotas serão renderizadas. A função `links` é usada para adicionar links de estilos (CSS) ao documento.

## Passo 4: Executando a Aplicação
1. **Iniciar o servidor de desenvolvimento:**
   - No terminal, execute `npm run dev` para iniciar o servidor de desenvolvimento.
   - Abra o navegador e acesse `http://localhost:3000` para ver a aplicação em ação. Você verá a mensagem "Hello, Remix!" centralizada na tela e estilizada com o CSS que você adicionou.
