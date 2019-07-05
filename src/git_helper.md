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

[![Banner](/src/assets/add-ssh.png)](https://github.com/deppbrazil/course-git-e-github-para-iniciantes/blob/master/dist/storage/criando-e-adicionando-uma-chave-ssh.md)

### Para abrir a chave gerada via terminal

- cd ~/ `volta para pasta raiz do sistema`
- cd .ssh/ `entra na pasta ssh onde vai estar a chave`
- ls `lista os arquivos`
- cat id_rsa.pub `abre o arquivo`

# Seção 3 - Essencial do Git

###Iniciando um repositório

- mkdir nome_da_pasta `cria pasta`
- cd nome_da_pasta `entra na pasta`
- git init `inicia arquivo .git`
- ls `mostra detalhes dos arqvuivos`

###Ciclo de vida no git

- untracked `não marcado, acabou de ser add no repo mas o git ainda não conhece o arquivo`
- unmodified `depois de add ao controle do git, porém não foi modificado`
- modified `passou por modificações`
- staged `quando enviado ao stage` depois commit

<img width="584" alt="screen shot" src="(/src/assets/file-status-lifecycle.png">

###Praticando

Vamos criar nosso primeiro repositório no github

<img width="584" alt="screen shot" src="(/src/assets/new-repo.png">

Podemos sincronizar nosso repositorio online com o local de duas formas:

#####1- Clonando o projeto do github

- git@github.com:andersonline2013/firstRepo.git `clona um projeto`

#####2- Sincronizando apartir do repositório local

- mkdir nome_da_pasta `cria pasta`
- cd nome_da_pasta `entra na pasta`
- echo "# firstRepo" >> README.md `cria o arquivo README`
- git init `inicia arquivo .git`
- git status `status do novo arquivo (untracked não esta marcado para envio)`
- git add README.md `envia o arquivo para o staged (pronto para o envio)`
- git commit -m "first commit" `commita os arquivo do staged`
- git remote add origin https://github.com/andersonline2013/firstRepo.git `sincroniza seu repositório local com o remoto`
- git push -u origin master `envia os arquivos para o repositório remoto`
