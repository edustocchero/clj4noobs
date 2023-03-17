# Executando arquivos

Vamos sair um pouco do nosso REPL e começarmos a escrever nosso código em arquivos.

O Clojure permite a execução de arquivos como scripts. Para isso, podemos executar o comando no terminal:
`clj -M [caminho do arquivo]`

> `clj -M foo.clj`

## Criando um arquivo

Você pode criar um arquivo com o nome de sua preferência, o arquivo deve conter a extensão `.clj`.

O padrão é que você crie arquivos com nomes em minúsculo e separados por underscores.

> Exemplo: meu_arquivo.clj

Agora vamos escrever um código simples e executá-lo:

```clj
(defn tudo-ok []
  (println "tudo ok"))

(tudo-ok)
```

Usando o comando `clj -M [caminho do seu arquivo]`, você verá a mensagem 'tudo ok' em seu terminal.

## Aumentando o repertório

Já que agora estamos escrevendo nosso código em arquivos, fica mais fácil de lermos e escrevermos funções com mais de 
uma linha.

Como já visto antes, para declararmos variáveis é necessario usar o `def`. O problema é que ela cria uma variável
global, que pode ser vista por outros namespaces.

> Logo mais iremos estudar sobre namespaces em Clojure.

Muitas vezes apenas queremos criar uma variável local, então podemos utilizar a função especial chamada `let`.

Essa função recebe um vetor, onde atribuímos um símbolo para um valor, como pares:

```clj
(let [nome "John"])
```

O `let` fará com que o símbolo **nome** exista apenas dentro dele. Então podemos utilizar a função `println` dentro do
`let` para exibirmos o valor de **nome**.

```clj
(let [nome "John"]
  (println nome))
```

Caso você precise definir mais valores, basta continuar atribuindo um símbolo para um valor em pares:

```clj
(let [nome "John"
      idade (* 4 5)]
  (println "nome:" nome "idade:" idade))
```

## Recapitulando

Vamos utilizar o que aprendemos até agora.

A função que iremos criar é a função para obtermos juros simples.

Para entendermos o que vamos precisar fazer, devemos olhar para a fórmula de juros simples: **J = C . i . t**.

Onde:
- C é o capital investido.
- i a taxa de juros.
- t o período de tempo.
- e J, os juros.

Começaremos definindo o que a função precisa receber como parâmetro.

```clj
(defn juros-simples [capital taxa periodo])
```

Primeiro, vamos obter a porcentagem da taxa.

```clj
(defn juros-simples [capital taxa periodo]
  (let [taxa-porcentagem (/ taxa 100)]))
```

Agora precisamos descobrir o valor da taxa acumulada. Iremos multiplicar a taxa pelo período de tempo.

```clj
(defn juros-simples [capital taxa periodo]
  (let [taxa-porcentagem (/ taxa 100)
        taxa-acumulada (* taxa-porcentagem periodo)]))
```

Para concluirmos, precisamos obter o rendimento aplicando a taxa acumulada no capital.

```clj
(defn juros-simples [capital taxa periodo]
  (let [taxa-porcentagem (/ taxa 100)
        taxa-acumulada (* taxa-porcentagem periodo)
        juros (* taxa-acumulada capital)]))
```

E também retornar o valor dos juros adicionando ele dentro do `let`.

```clj
(defn juros-simples [capital taxa periodo]
  (let [taxa-porcentagem (/ taxa 100)
        taxa-aplicada (* taxa-porcentagem periodo)
        juros (* taxa-aplicada capital)]
    juros))
```

O `let` irá retornar o último valor dentro do seu corpo, nesse caso, os juros, que será retornado também pela nossa
função `juros-simples`.

Podemos testar nossa função agora:

```clj
(let [capital 3400
      taxa    6
      periodo 4]
  (println (juros-simples capital taxa periodo)))
```
