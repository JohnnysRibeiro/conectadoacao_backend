# Backend do ConectaDoacao

## Configurações Ruby
### Instale o RVM, versionador de rubies
Instale GPG keys:

```gpg2 --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB```

Instale o RVM

```\curl -sSL https://get.rvm.io | bash -s stable```

Para utilizarmos o comando rvm no terminal é preciso fazer uma pequena alteração no terminal clicando em “Editar”, depois “Preferências do Perfil”, clique na aba “Titulo e comando” e marque “Executar comando como shell de sessão”. Reinicie seu terminal

### Instale o Ruby e o bundler
Instale o ruby passando a versão do projeto

```rvm install 2.6.3```

Instale o bundle

```gem install bundler```

## Banco de dados

O banco utilizado neste projeto é o postgres. 
No Linux, é possível instalar o postgres com

``sudo apt-get install postgresql postgresql-contrib``

Acesse o banco postgres com o usuário padrão postgres:

``sudo -u postgres psql``

Crie um usuario para manipular o banco:

``create role conectadoacao_back_user with createdb password '123123' login;``
Crie o banco, setando como owner o usuário criado anteriormente:

``create database conectadoacao_back_development with owner conectadoacao_back_user encoding 'unicode';``

Saia do postgres e faça a migração das tabelas:

``rake db:migrate``