# Conhecendo a linguagem

Caso a instalação do Clojure tenha sido um sucesso, ao digitar `clj` em seu terminal você verá um REPL interativo:

```clj
Clojure 1.11.1
user=>
```

O REPL é uma ferramenta que utilizamos sempre, ele nos permite evaluar nosso código de forma simples e rápida.

Agora, vamos conhecer os tipos primitivos de Clojure?

## Números

```clj
user=> 42 ; int / inteiros
42

user=> 3.14 ; floating point / ponto flutuante
3.14

user=> 17/3 ; ratio / razão
17/3
```

> Comentários podem ser feitos usando ponto e vírgula, `;`.

## Caracteres

Strings ficam dentro de aspas duplas `""` e podem estar contidas em multiplas linhas.

Caracteres são representados com um `\` na frente, como `\w` e também `\newline`, pois alguns caracteres possuem
nomes especiais.

Expressões regulares são strings com um `#` no início e transformam-se em um objeto Java `java.util.regex.Pattern`.

```clj
user=> "olá!"    ; string
"olá!"

user=> \w        ; character / caractere
\w

user=> #"[0-9]+" ; regular expression / expressões regulares
```

## Símbolos

Os símbolos são usados para nos referirmos a algo, podendo ser uma função, um valor definido ou um namespace.

```clj
user=> +
#object[...]

user=> clojure.core/+
#object[...]
```

## Keywords

As keywords são um tipo especial de símbolo, elas sempre possuem dois pontos `:` na frente.

O valor de uma keyword é a própria keyword.

Iremos utilizá-las principalmente em mapas.

```clj
user=> :ok
:ok
```

## Valor nulo e Booleanos

O valor nulo, verdadeiro e falso são `nil`, `true` e `false`, respectivamente.

```clj
user=> nil
nil

user=> true
true

user=> false
false
```

## Coleções

O Clojure possui apenas 4 tipos de coleções: listas, vetores, conjuntos e mapas.

```clj
user=> '(1 2 3 4)       ; listas
(1 2 3 4)

user=> [1 2 3]          ; vetores
[1 2 3]

user=> #{1 2 3}         ; conjuntos
#{1 2 3} ; pode não aparecer em ordem correta

user=> {:a 1 :b "dois"} ; mapas
{:a 1 :b "dois"}
```

> Logo iremos comentar sobre o apóstrofo `'` antes dos parêntesis na lista.

## Usando funções

Para invocarmos uma função precisamos de uma lista, um símbolo de uma função e seus argumentos:

```clj
(+ 1 2)

() -> chamada / lista

+ -> símbolo / função de soma

1 -> argumento / número
2 -> argumento / número
```

```clj
user=> (+ 1 2)
3
```

O Clojure entende que tudo o que estiver dento de parêntesis é uma invocação de função.

Por isso na estrutura de lista nós utilizamos o apóstrofo `'`, ele é um símbolo de 'quoting', serve para que o código 
não seja evaluado.

```
user=> '(+ 1 2)
(+ 1 2)
```

Caso você tente evaluar uma lista, irá se deparar com um erro em seu REPL.

```clj
user=> (1 2 3)
Execution error (ClassCastException) at user/eval1 (REPL:1).
class java.lang.Long cannot be cast to class clojure.lang.IFn
```

Ao lermos a mensagem de erro, vamos perceber que não é possível transformar um Long em uma IFn.
