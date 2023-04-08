# Aninhando mapas

Em Clojure acaba sendo normal aninharmos coleções, principalmente os mapas.

Como é de se esperar, a linguagem já nos fornece funções e funcionalidades para facilitar nossa vida.

## `assoc-in`

Utilizamos o `assoc-in` para associar valores quando precisamos percorrer mais de uma chave em um mapa.

```clj
(def mercurio {:gravidade   3.6
               :temperatura "166C"})

(def sistema {:nome "Sistema Solar"
              :sistema
              {"Sol" {:gravidade   27.4
                      :temperatura "5778K"}}})
```

A função irá receber o mapa seguido de um vetor com as chaves, sendo a última a nova chave a ser associada e o valor
da nova chave.

Nesse caso vamos querer associar mais um corpo celeste na chave `:sistema`, então podemos fazer:

```clj
(def sistema-novo (assoc-in sistema [:sistema "Mercurio"] mercurio))

(println sistema-novo)
```

## `get-in`

Já que podemos aninhar valores também podemos pegar valores aninhados.

Similar a função anterior, precisamos passar o mapa e um vetor de chaves para recuperarmos um valor aninhado.

```clj
(def sol (get-in sistema-novo [:sistema "Sol"]))

(println sol)
```

## `update-in`

Caso seja necessário alterarmos apenas um valor em um mapa aninhado, utilizamos o `update-in`.

```clj
(def sistema-novo (update-in sistema-novo [:sistema "Mercurio" :gravidade] 3.7))
```
