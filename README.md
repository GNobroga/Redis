# REDIS

O Redis é um banco de dados em memória (NoSQL) que trabalha com o conceito de chave e valor. Além disso, as consultas
são baseadas em chaves.

## Comandos

Esse é o comando pra abrir interação com a CLI do Redis para executar comandos.

```bash
    redis-cli
```

### Exibir keys

Mostra todas as chaves disponíveis

```bash
    KEYS *
```

Além disso é possível filtrar keys com base em critérios

**\*** - É o coringa pra representar qualquer caracter que vier em seguida.

**?** - Represente um único caracter.

**[]** - Permite especificar caracteres e servir como uma operação um ou outro.

```bash
    KEYS name*idade??joao[ab]
```

**HKEYS** - Serve pra exibir keys definidos com o comando **HSET**

```bash
    HKEYS field
```


### SET 


O comando SET permite adicionar elemento.

```bash
    SET key value
```

O comando **MSET** permite definir vários elementos em um único comando.

```bash
    MSET key value key value key value
```

O comando **HSET** permite definir um atributo para um hash.

```bash
    HSET hash key value key 
```

O comando **HMSET** permite definir vários atributos para um hash.

```bash
    HMSET hash key value key value key value
```

### GET 


**GET** - Serve para obter o valor de uma **key**

```bash
    GET key
```

**HGET** - Serve para obter o valor de uma key dentro de um hash

```bash
    HGET field key
```

**HGETALL** - Permite obter todos os elementos contidos no hash

```bash
    HGETALL field 
```

No exemplo abaixo ele trás todos os chaves e valor contidos no hash.

![Alt text](/img/image-3.png)

Para visualizar um valor, por exemplo, vou usar a chave nome

```bash
    HGET produto valor 
```
A saída vai ser 100

## DEL

**DEL** - Permite deletar uma key

```bash
    DEL key
```

**HDEL** - Permite deletar um hash

```bash
    HDEL hash
```

<hr>

## Listas 

**LPUSH (Left Push)** - Serve pra criar e adicionar elementos em uma lista, sempre adiciona à esquerda. Caso a lista já exista, mais elementos serão adicionados nela.

```bash
    LPUSH key element [element...]
```

![Alt text](/img/image.png)

![Alt text](/img/image-1.png)

**LINDEX** - Serve para pegar um elemento da lista 

```bash
    LINDEX key index
```

![Alt text](/img/image-2.png)

**LLEN** - Pra pegar o tamanho da lista

```bash
   LLEN key 
```

**RPUSH** - Serve para adicionar no final da lista

```bash
   RPUSH key element [...element]
```

**LRANGE** - Serve para pegar os valores de uma lista através de um range

No exemplo abaixo, pega do index 0 até o index 2.

```bash
   LRANGE key 0 2
```

**LTRIM** - Serve para recortar a lista

O comando abaixo irá remover do index 0 até o 2

```bash
   LTRIM key 0 2
```

**LPOP** - Serve para remover do início da lista

```bash
   LPOP key
```

**RPOP** - Serve para remover do fim da lista

```bash
   RPOP key
```


## Filas

Quando utilizamos **RPUSH** e **LPOP** estamos criando uma fila. 

**BLPOP (Block)** - O comando BLPOP no Redis é utilizado para bloquear uma conexão até que um elemento seja inserido na lista, ou até que o tempo de timeout seja atingido. Depois desse timeout ele remove o elemento.

```bash
    BLPOP key timeout
```

Especificar pra aguardar pra sempre até um elemento ser adicionado a fila 

```bash
    BLPOP key 0
```

### Limpar Banco

Limpa todos os dados do banco selecionado

```bash
    FLUSHDB
```

Limpa todos os dados de todos os bancos

```bash
    FLUSHALL
```

### Bancos

O Redis ele vem com 15 bancos de dados diferentes enumerados de 0 até 15.

**SELECT** - Para selecionar um dos bancos

```bash
    SELECT 0
```

### Outros comandos

**TYPE** - Serve para verificar o tipo do valor que a chave armazena

```bash
    TYPE key
```

**EXISTS** - Verificar se existe uma chave

Retorna 1 ou 0

```bash
    EXISTS key
```
