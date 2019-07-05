[Voltar](/README.md)

[![Banner](/src/assets/banner.jpg)](https://github.com/andersonline2013/Estudo/blob/master/src/git_helper.md)

# Seção 1 - Instalando o Git

### Instalação e criação de conta

- [Download](https://git-scm.com/download)

- [Criar conta GitHub](https://github.com/join)

# Seção 2 - Configurando o Git

### Configurando o acesso do git ao github

Abra o Git Bash Here

Definir usuário

```
git config --global user.name "Seu Nome"
```

Definir email

```
git config --global user.email "seuemail@gmail.com"
```

### Criando e adicionando a chave ssh

##### [Documentação](https://help.github.com/articles/connecting-to-github-with-ssh/)

- ssh-keygen `para gerar par de chaves`
- para os demais passos `enter`
- pronto abrir o arquivo `id_rsa.pub` na pasta de usuário no pc e adicionar no Github em:

[![Banner](/src/assets/add-ssh.png)](https://github.com/andersonline2013/Estudo/blob/master/src/git_helper.md)

### Para abrir a chave gerada via terminal

- cd ~/ `volta para pasta raiz do sistema`
- cd .ssh/ `entra na pasta ssh onde vai estar a chave`
- ls `lista os arquivos`
- cat id_rsa.pub `abre o arquivo`

# Seção 3 - Essencial do Git

### Iniciando um repositório

- mkdir nome_da_pasta `cria pasta`
- cd nome_da_pasta `entra na pasta`
- git init `inicia arquivo .git`
- ls `mostra detalhes dos arqvuivos`

### Ciclo de vida no git

- untracked `não marcado, acabou de ser add no repo mas o git ainda não conhece o arquivo`
- unmodified `depois de add ao controle do git, porém não foi modificado`
- modified `passou por modificações`
- staged `quando enviado ao stage` depois commit

[![Banner](/src/assets/file-status-lifecycle.png)](https://github.com/andersonline2013/Estudo/blob/master/src/git_helper.md)

# Seção 4 - Sincronização de repositórios

Vamos criar nosso primeiro repositório no github

[![Banner](/src/assets/new-repo.png)](https://github.com/andersonline2013/Estudo/blob/master/src/git_helper.md)

## Podemos sincronizar nosso repositorio online com o local de duas formas:

### 1- Clonando o projeto do github

- git clone git@github.com:andersonline2013/firstRepo.git `clona um projeto`

### 2- Sincronizando apartir do repositório local

- mkdir nome_da_pasta `cria pasta`
- cd nome_da_pasta `entra na pasta`
- echo "# firstRepo" >> README.md `cria o arquivo README`
- git init `inicia arquivo .git`
- git status `status do novo arquivo (untracked não esta marcado para envio)`
- git add README.md `envia o arquivo para o staged (pronto para o envio)`
- git commit -m "first commit" `commita os arquivo do staged`
- git remote add origin https://github.com/andersonline2013/firstRepo.git `sincroniza seu repositório local com o remoto`
- git push -u origin master `envia os arquivos para o repositório remoto`

# Seção 5 - Ramificação (Branch)

O que é uma branch? é um ponteiro móvel que leva um commit, ou seja, para conserto de bugs ou features, o ideal é criar uma branch separada para não comprometer a branch master, e quando aprovado fazer o merge com a master.

#### Comandos para branch

- git checkout -b <nome do branch> # Seção 6 - Principais comandos
- git branch `lista as branches existentes (* indica qual é a branch atual)`
- git branch -D <nome do branch> `apaga a branch localmente`
- git push origin <nome do branch> --delete || git push origin :<nome do branch> `apaga a branch remotamente`

# Seção 6 - Principais comandos

- git status `visualizar o status dos arquivos alterados no repositório local`
- git add . `inclui no staged os arquivos alterados`
- git commit -m "Comments" `inclui um comentario ao commit`
- git push origin "branch" `envia para o repositório remota as alterações efetuadas`
- git pull origin "branch" `baixa as atualização do repositório remoto para o local`

# Seção 7 - Praticando

Vamos entender esse conceito praticando.

No seu projeto crie um arquivo chamado **destructuring.js** com o seguinte conteudo:

```js
const cat = {
  name: "Alfred",
  breed: "Persian"
};
```

Commit ao novo arquivo para a branch master

```
git add .
git commit -m "Incluido novo arquivo destructuring.js"
git push origin master
```

Crie uma nova branch chamada tarefa45

```
git checkout -b tarefa45
```

Altere o arquivo **destructuring.js**

```js
const cat = {
  name: "Alfred",
  breed: "Persian"
};

const { name, breed, age = 3 } = cat;
//name = Alfred
//breed = Persian
//age = 3
```

Commit as alterações para a branch tarefa45

```
git add .
git commit -m "Finalização da tarefa 45"
git push origin tarefa45
```

Mescle a nova branch "tarefa45" na branch principal "manster"

```
git checkout master
git merge tarefa45
```

Commit as alterações para a branch master

```
git add .
git commit -m "merge tarefa45"
git push origin master
```

Apague a branch "tarefa45

```
git push origin :tarefa45
```

# Seção 7 - Conflitos

Crie uma nova branch chamada #conflito

```
git checkout -b #conflito
```

Altere o arquivo **destructuring.js**

```js
const cat = {
  name: "Alfred Marcus",
  breed: "Persian"
};

const { name: fullname, breed, age: yearsOld = 3 } = cat;
//fullname = Alfred
//breed = Persian
//yearsOld = 3
```

Commit as alterações para a branch #conflito e volte para a branch master

> git -am adiciona e commita ao mesmo tempo

```
git commit -am "Alterado o nome das propriedades do obj cat"
git push origin #conflito
git checkout master
```

Altere o arquivo **destructuring.js** na branch master

```js
const cat = {
  name: "Alfred",
  breed: "Persian"
};

const cities = {
  paris: {
    country: "France",
    language: "French"
  },
  brazil: {
    country: "Brazil",
    language: "Portuguese"
  }
};

const { name, breed, age = 3 } = cat;
//name = Alfred
//breed = Persian
//age = 3
const {
  brazil: { country },
  paris
} = cities;
//country = Brazil
//paris = {country: 'France', language: 'French'}
```

Suba as alterações para o repositóro remoto

```
git commit -am "incluido obj cities"
git push origin master
```

Mescle a branch #conflito na branch master

```
git merge #conflito
```

Agora nos deparamos com um conflito...

[![Banner](/src/assets/merge.gif)](https://github.com/andersonline2013/Estudo/blob/master/src/git_helper.md)

O git ira separar os conflitos da seguinte forma
`<<<<<<< HEAD`
`conteudo da branch master`
`=======`

`=======`
`conteudo da branch #conflito`
`>>>>>>> 98663bb97c1053ed8cc0cc3961a16972a2656e4f`

Resolva o conflito e commit as alterações

```
git commit -am "merge #conflito"
git push origin master
```
