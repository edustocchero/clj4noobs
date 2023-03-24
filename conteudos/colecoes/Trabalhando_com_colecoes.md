# Trabalhando com coleções

Como visto anteriormente, o Clojure possui quatro tipos de coleções: listas, vetores, conjuntos e mapas.

Para trabalharmos com estas estruturas, a linguagem nos fornece diversas funções para manuseá-las. 
Vamos ver algumas dessas funções agora.

## `get`

O `get` é uma função que necessita de uma sequência e um índice.
Ele irá nos retornar o elemento presente no índice ou `nil`.

```clj
(def meu-vetor ["um" :dois 3])

(let [elemento (get meu-vetor 0)]
  (println elemento))
```

> Em Clojure, o índice do primeiro elemento começa em 0.

Uma sequência pode ser tanto um vetor como um conjunto.

Também podemos utilizar o `get` para acessarmos um valor presente em um mapa através de sua chave.

```clj
(def pessoa {:nome      "John"
             :sobrenome "Doe"
             :gostos    #{"Musica" "Livros" "Video Games"}})

(let [nome (get pessoa :nome)
      gostos (get pessoa :gostos)]
  (println nome)
  (println gostos))
```

Também podemos providenciar um valor padrão caso o índice ou chave não exista.

```clj
(let [elemento (get meu-vetor 3 "Não existe")]
  (println elemento))
```

## `count`

O `count`, como esperado, é uma função que irá retornar a quantidade de elementos presentes em uma coleção.

```clj
(let [qnt (count meu-vetor)]
  (println "Meu vetor tem" qnt "elementos"))
```

Caso você passe um mapa para o `count`, ele irá contar a ocorrência dos pares (chave e valor) presentes no mapa,
ignorando aninhamentos.

## `conj` e `disj`

`Conj`, do verbo em inglês conjoin (juntar/unir), irá juntar valores dependendo da estrutura de dados passada.

O `conj` irá receber a coleção seguida dos valores que você quer adicionar.

```clj
(let [juntado (conj [1 2 3] 4 5 6)]
  (println juntado))
```

> Você pode encontrar mais exemplos e ver como as diferentes estruturas de dados se comportam com o `conj`
[clicando aqui](https://clojuredocs.org/clojure.core/conj).

O `disj` (disjoin), faz o contrário do conjoin, ele irá remover o(s) valor(es), porém pode ser utilizado apenas em
conjuntos.

```clj
(let [numeros #{1 2 3 4}
      numeros (disj numeros 3 1)]
  (println numeros))
```

## `first`, `second`, `nth` e `rest`

As listas em Clojure são listas ligadas, não conseguimos acessar um índice em específico usando o `get`. Mas podemos
utilizar o `nth`.

```clj
(let [lista '(0 1 2 3)
      segundo (nth lista 1)]
  (println segundo))
```

Para acessarmos o primeiro (cabeça) ou segundo elemento de uma lista ligada podemos utilizar o `first` e o `second`.

```clj
(let [lista '(0 1 2 3)
      primeiro (first lista)
      segundo (second lista)]
  (println "primeiro:" primeiro "segundo:" segundo))
```

Para pegarmos apenas o resto (cauda) de uma lista, utilizamos o `rest`.

```clj
(let [lista '(0 1 2 3)
      resto (rest lista)]
  (println resto))
```

## `assoc` e `dissoc`

O `assoc` (associate), serve para associarmos uma chave para um valor em um mapa.

```clj
(def endereco {:logradouro "Praça da Sé"
               :uf         :sp
               :local      "São Paulo"
               :bairro     "Sé"})

(let [com-cep (assoc endereco :cep "01001-000")]
  (println com-cep))
```

> Veja mais exemplos com o `assoc` [clicando aqui](https://clojuredocs.org/clojure.core/assoc).

Enquanto o `dissoc` (dissociate), serve para dissociarmos uma chave-valor através de uma chave.

```clj
(let [sem-bairro (dissoc endereco :bairro)]
  (println sem-bairro))
```

> Veja mais exemplos com o `dissoc` [clicando aqui](https://clojuredocs.org/clojure.core/dissoc).
