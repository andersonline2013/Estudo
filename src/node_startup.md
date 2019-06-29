[Voltar](/Readme.md)

# Node.js

Node.js é uma plataforma construída sobre o motor JavaScript do Google Chrome para facilmente construir aplicações de rede rápidas e escaláveis. Node.js usa um modelo de I/O direcionada a evento não bloqueante que o torna leve e eficiente, ideal para aplicações em tempo real com troca intensa de dados através de dispositivos distribuídos.

[Referência](http://nodebr.com/o-que-e-node-js/)

# Iniciando projeto Node

Criar a pasta para o projeto e acessa-lá através da linha de comando. Executar o seguinte comando para iniciar o projeto node.js

```
yarn init -y
```

> O -y indica para criar os arquivos com os valores default
> Será criado o arquivo **package.json** com as informações do projeto.

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
