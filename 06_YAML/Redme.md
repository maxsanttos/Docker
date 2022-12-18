# YAML

## O QUE É YAML

Uma linguagem de serialização, seu nome é **YAML ain't Markup Language**(YAML não é uma linguagem de marcação);

Usada gerelmente para arquios de configuração,inclusive do Docker, para configuurar o **DOCKER COMPOSE**;

É de fácil leitura para nós humanos;

A extensão dos arquivos é **yml ou yaml**;

## Criando nosso arquivo YAML

O arquivo **.yaml** geralmente possui chaves e valores;

Que é de onde vamos retirar as configuração do nosso sistema;

Para definir uma chave apenas inserimos o nome dela, em seguida colocamos **dois pontos e depois o valor**;

VAmos criar nosso primeiro arquivo YAML!

## Espaçamento e identificação

O **fim de uma linha** indica o fim de uma instrução, não há ponto e vírgula;

A indentação deve conter **um ou mais espaços** e não devemos utilizar tab;

E cada uma define um novo bloco;

O **espaço é obrigatório** após a declaração da chave;

Vamos ver na prática!

## Comentários no YAML

Podemos escrever comentários em YAML também, utilizando o símbolo **#**;

O processador de YAML **ignora comentários**;

Eles são úteis para escrever como o arquivo funciona/foi configurado;

## Dados numéricos

Em YAML podemos escrever dados numéricos com:

* **Inteiros** = 12;
* **Floats** = 15.8;

## Strings no YMAL

Em YAML podemos escrever textos de duas formas:

* **Sem aspas**: este é um texto válido
* **Com aspas**:"e este também"

## Valores nulos

Em YAML podemos definir um dado como nulo de duas formas:

* **~ ou null**

* Os dois vão resultar em None, após a interpretação

## Booleanos

Podemos inserir booleanos em YAML da seguinte forma:

* **True e On** = verdadeiro;
* **False e Off** = falso;

## Lista

### Arrays

Os arrays, tipos de dados para listas, possuem duas sintaxes:

* Primeira:**[1,2,3,4,5]**
* Segunda:

```exemplo
items:
 - 1
 - 2
 - 3
```

## Dicionários

* Os dicionários, tipo de dados para objetos ou lista com chaves e valores, podem ser escritos assim:

* obj:{a:1,b:2,c:3}

* E também com o nesting:

Objeto:
    chave: 1
    chave: 2
