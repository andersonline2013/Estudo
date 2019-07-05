[Voltar](/README.md)

[![Banner](/src/assets/banner.jpg)](https://github.com/andersonline2013/Estudo/blob/master/src/git_helper.md)

### Seção 1 - Instalando o Git

# Instalação c criação de conta

- [Download](https://git-scm.com/download)

- [Criar conta GitHub](https://github.com/join)

### Seção 2 - Configurando o Git

Definir usuário

```
git config --global user.name "Seu Nome"
```

Definir email

```
git config --global user.email "seuemail@gmail.com"
```

### [Documentação](https://help.github.com/articles/connecting-to-github-with-ssh/)

- ssh-keygen `para gerar par de chaves`
- para os demais passos `enter`
- pronto abrir o arquivo `id_rsa.pub` na pasta de usuário no pc e adicionar no Github em:

[![Banner](/src/assets/add-ssh.png)](https://github.com/deppbrazil/course-git-e-github-para-iniciantes/blob/master/dist/storage/criando-e-adicionando-uma-chave-ssh.md)

### Para abrir a chave gerada via terminal (po)

- cd ~/ `volta para pasta raiz do sistema`
- cd .ssh/ `entra na pasta ssh onde vai estar a chave`
- ls `lista os arquivos`
- cat id_rsa.pub `abre o arquivo`

## Instalando o Express

Para disponibilizar serviços para ser consumidos pelos front-ends, será usado o pacote **express**, esse pacote é utilizado para controlar as requisições (rotas) no servidor.

> Express é um framework para Node.js inspirado no Sinatra. Ele é minimalista, flexível e contém um robusto conjunto de recursos para desenvolver aplicações web, um robusto sistema de roteamento e views.

Instalar o pacote express

```
yarn add express
```

## Configurações do Ambiente de desenvolvimento

# Configurando ESLint

ESLint é um gerenciador de código, deixando todos os códigos feitos por diversos desenvolvedores com o mesmo padrão. Isso garante uma padronização no código fonte da aplicação independentemente do desevolvedor.

## Instalando ESLint

Necessário estar com as extensões **eslint** e **prettier** instaladas no vscode.

Adicionar o pacote eslint em modo de desenvolvimento

```
yarn add eslint -D
```

Iniciar o eslint

```
npx eslint --init
```

---

Nesse momento será exibido no terminal algumas perguntas para que o eslint entenda qual será o padrão de código que será utilizado no projeto.

### How would you like to use ESLint?

- [ ] To check syntax only
- [ ] To check syntax and find problems
- [x] To check syntax, find problems, and enforce code style

### What type of modules does your project use?

- [ ] JavaScript modules (import/export) **(React | React-Native)**
- [ ] CommonJS (require/exports) **(Node)**
- [ ] None of these

> Caso esteja em um projeto node, utilize a segunda opção, caso seja um projeto React ou ReactNative usar a primeira opção.

### Which framework does your project use?

- [ ] React **(React | React-Native)**
- [ ] Vue.js
- [ ] None of these **(Node)**

> Caso esteja em um projeto node, utilize a terceira opção, caso seja um projeto React ou ReactNative usar a primeira opção.

### Where does your code run?

- [ ] Browser **(React.js)**
- [ ] Node **(node)**

> Caso esteja em um projeto node, utilize a segunda opção, caso seja um projeto React marque a primeira oopção, caso seja ou ReactNative deixa sem marcar as duas opções.

### How would you like to define a style for your project?

- [x] Use a popular style guide
- [ ] Answer questions about your style
- [ ] Inspect your JavaScript file(s)

### Which style guide do you want to follow?

- [x] Airbnb (https://github.com/airbnb/javascript)
- [ ] Standard (https://github.com/standard/standard)
- [ ] Google (https://github.com/google/eslint-config-google)

### What format do you want your config file to be in?

- [ ] JavaScript
- [ ] YAML
- [x] JSON

### Would you like to install them now with npm? (Y/n)

- Y

> Y para informar que deseja utilizar o npm para instalação dos pacotes

---

Após a instalação dos pacotes, remova o arquivo **package-lock.json** e execute o comando

```
yarn
```

Isso atualizará os pacotes conforme o instalador yarn

---

# EditorConfig

EditorConfig é um arquivo que adicionado ao projeto, garante que o desenvolvedor que estiver utilizando o editor, tenha as mesmas configurações de linha, espaçamentos, salto de linha, isso indepentemente de qual editor esteja utilizando, seja vscode, sublime, etc.

## Configurando

- Adicionar extensão do editorconfig.

Adicionar o arquivo **.editorconfig** na raiz do projeto com as seguintes informações:

```
root = true

[*]
indent_style = space
indent_size = 2
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
end_of_line = lf
```

--

## Arquivo de Variáveis Ambiente

Instale o pacote

```
yarn add dotenv
```

Crie o arquivo **.env** na raiz da aplicação

> Esse arquivo é responsável por armazenar todas as variáveis do ambiente, por exemplo: PORT, NODE_ENV, etc.

Com os seguintes códigos:

```
NODE_ENV=Development
PORT=3000
```

--

## Configurando estrutura das pastas

No editor é comum separar os arquivos criados pelo desenvolvedor, dos arquivos de estrutura de funcionamento do projeto. Para isso é necessário criar a pasta **src** na raiz do projeto, onde serão armazenados todos os arquivos para o projeto.

Criar o arquivos: routes.js, server.js e index.js dentro da pasta **src**

Arquivo **routes.js**

```js
const express = require("express");

const routes = express.Router();

routes.get("/", (req, res) => res.send("Hello World"));

module.exports = routes;
```

Arquivo **server.js**

```js
const express = require("express");
const routes = require("./routes");

class App {
  constructor() {
    this.express = express();
    this.isDev = process.env.NODE_ENV !== "production";

    this.middlewares();
    this.routes();
  }

  middlewares() {
    this.express.use(express.json());
  }

  routes() {
    this.express.use(routes);
  }
}

module.exports = new App().express;
```

Arquivo **index.js**

```js
require("dotenv").config();
const server = require("./server");

const port = process.env.PORT || 3000;
server.listen(port, () => {
  console.log(`Environment is ${process.env.NODE_ENV}`);
  console.log(`App listening to port ${port}....`);
  console.log("Press Ctrl+C to quit.");
});
```

--

# Nodemon

Nodemon é um file watcher, que roda internamente o próprio comando node. Dessa forma toda e qualquer atualização é executada automaticamente, sem a necessidade de parar e rodar o node novamente.

## Instalando o Nodemon

Adicionar o pacote **nodemon** em modo de desenvolvimento

```
yarn add nodemon -D
```

Adicionar o seguinte script para inicialização do nodemon. Adicionar o script dentro do **package.json**

```json
"scripts": {
  "start": "nodemon src/index.js"
}
```

Por padrão utilizamos "start" no script, dessa forma quando executar o comando, não precisará escrever node index.js e sim yarn start.

```
yarn start
```

Para parar o monitoramento aperte

```
Ctrl + C
```

## Testando o serviço

Executar o comando

```
yarn start
```

Abrir o navegar no endereço [http://localhost:3000](http://localhost:3000). Deverá aparecer o texto **Hello World**
