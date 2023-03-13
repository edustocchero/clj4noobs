# Explorando o clojure.core

O clojure.core é a biblioteca padrão do Clojure, ela irá nos disponibilizar funcionalidades básicas para criarmos
nossas aplicações.

## Definindo uma variável

Para criarmos uma "variável" iremos utilizar o `def`, uma função especial que irá criar uma variável imutável e
acessível no namespace atual.

Voltando para nosso REPL, o `def` precisa receber o nome e valor da nossa variável, como você pode ver abaixo:

```clj
user=> (def um 1)
#'user/um
```

> Você pode ver mais exemplos usando o `def` [clicando aqui](https://clojuredocs.org/clojure.core/def).

Evaluando o def no REPL, ele irá retornar o nome completo do símbolo, nesse caso `user/um`.

Para obtermos o valor da variável podemos usar o nome completo do símbolo:

```clj
user=> user/um
1
```

Mas como nosso REPL está no namespace **user**, podemos apenas usar o símbolo `um`.

```clj
user=> um
1
```

Agora podemos utilizar nossa variável em funções:

```clj
user=> (+ um 2 3)
6

user=> (type um)
java.lang.Long
```

Mas note que uma vez definido, seu valor nunca irá mudar.

```clj
user=> um
1
```

## Primeira função

Assim como o `def`, também existe outra função especial para definirmos nossas funções, o `defn`.

Para definirmos uma função vamos precisar de seu nome, um vetor com seus parâmetros e seu corpo:

```clj
user=> (defn dizer-ola [nome] (println "Olá," nome "!"))
#'user/dizer-ola
```

Definimos o símbolo `dizer-ola` para uma função que recebe um parâmetro (nome) e retorna a chamada da função `println`
com os argumentos ("Olá,", nome, "!").

> A função `println` está disponível através do core da linguagem.
> Você pode ver mais exemplos usando o `println` [clicando aqui](https://clojuredocs.org/clojure.core/println).

Podemos invocá-la com a sintaxe que já vimos antes:

```clj
user=> (dizer-ola "mundo")
Olá, mundo !
nil
```

Repare que além da função escrever na tela, ela retorna o valor `nil`, pois ela está retornando o retorno da chamada
da última expressão do seu corpo, o `(println ...)`, que retorna `nil`.

Também veja que o nome usado para definir a função `dizer-ola` está sendo separado por hífens. O nome desse padrão é
kebab-case, e em Clojure iremos segui-lo para nomear **funções** e **variáveis**.

> Você pode ver todas as funções disponíveis do clojure.core com exemplos através do
> [ClojureDocs](https://clojuredocs.org/clojure.core).
