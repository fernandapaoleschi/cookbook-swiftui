# Operadores em SwiftUI

Em programação, **operadores** são símbolos usados para realizar operações com valores, variáveis e constantes.

No Swift, usamos operadores para fazer cálculos, comparar valores, criar condições e atualizar dados.

No SwiftUI, operadores aparecem bastante em textos, botões, condições, cálculos e mudanças de estado.

---

## 1. O que são operadores?

Operadores são símbolos que executam alguma ação.

Exemplo:

```swift
let soma = 10 + 5
```

Nesse exemplo, o operador `+` soma os valores `10` e `5`.

Resultado:

```txt
15
```

---

## 2. Operadores aritméticos

Os operadores aritméticos são usados para realizar cálculos matemáticos.

| Operador | Nome | Exemplo | Resultado |
|---|---|---|---|
| `+` | Soma | `10 + 5` | `15` |
| `-` | Subtração | `10 - 5` | `5` |
| `*` | Multiplicação | `10 * 5` | `50` |
| `/` | Divisão | `10 / 2` | `5` |
| `%` | Resto da divisão | `10 % 3` | `1` |

---

## 3. Soma

O operador `+` é usado para somar valores.

```swift
let numero1 = 10
let numero2 = 5

let resultado = numero1 + numero2

print(resultado)
```

Resultado:

```txt
15
```

---

## 4. Subtração

O operador `-` é usado para subtrair valores.

```swift
let pontosIniciais = 100
let pontosPerdidos = 25

let pontosFinais = pontosIniciais - pontosPerdidos

print(pontosFinais)
```

Resultado:

```txt
75
```

---

## 5. Multiplicação

O operador `*` é usado para multiplicar valores.

```swift
let quantidade = 4
let preco = 10

let total = quantidade * preco

print(total)
```

Resultado:

```txt
40
```

---

## 6. Divisão

O operador `/` é usado para dividir valores.

```swift
let total = 100
let pessoas = 4

let valorPorPessoa = total / pessoas

print(valorPorPessoa)
```

Resultado:

```txt
25
```

---

## 7. Resto da divisão

O operador `%` retorna o resto de uma divisão.

```swift
let numero = 10

let resto = numero % 3

print(resto)
```

Resultado:

```txt
1
```

Esse operador é muito usado para verificar se um número é par ou ímpar.

```swift
let numero = 8

if numero % 2 == 0 {
    print("Número par")
} else {
    print("Número ímpar")
}
```

Resultado:

```txt
Número par
```

---

## 8. Operadores aritméticos em SwiftUI

Podemos usar operadores para exibir cálculos diretamente na tela.

```swift
import SwiftUI

struct ContentView: View {
    let nota1 = 8.0
    let nota2 = 9.0
    
    var media: Double {
        (nota1 + nota2) / 2
    }
    
    var body: some View {
        Text("Média: \(media)")
    }
}
```

Resultado:

```txt
Média: 8.5
```

---

## 9. Operadores de atribuição

Os operadores de atribuição são usados para atribuir ou atualizar valores.

| Operador | Significado | Exemplo |
|---|---|---|
| `=` | Atribui valor | `nome = "Marina"` |
| `+=` | Soma e atribui | `contador += 1` |
| `-=` | Subtrai e atribui | `contador -= 1` |
| `*=` | Multiplica e atribui | `total *= 2` |
| `/=` | Divide e atribui | `total /= 2` |

---

## 10. Atribuição simples

O operador `=` atribui um valor a uma variável.

```swift
var nome = "João"

nome = "Carlos"

print(nome)
```

Resultado:

```txt
Carlos
```

---

## 11. Soma e atribuição

O operador `+=` soma um valor e atualiza a variável.

```swift
var contador = 0

contador += 1

print(contador)
```

Resultado:

```txt
1
```

Isso é o mesmo que escrever:

```swift
contador = contador + 1
```

---

## 12. Subtração e atribuição

O operador `-=` subtrai um valor e atualiza a variável.

```swift
var vidas = 3

vidas -= 1

print(vidas)
```

Resultado:

```txt
2
```

---

## 13. Operadores de atribuição em SwiftUI

No SwiftUI, é comum usar operadores de atribuição dentro de botões.

```swift
import SwiftUI

struct ContentView: View {
    @State private var contador = 0
    
    var body: some View {
        VStack(spacing: 16) {
            Text("Contador: \(contador)")
            
            Button("Aumentar") {
                contador += 1
            }
            
            Button("Diminuir") {
                contador -= 1
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- `contador += 1` aumenta o valor em 1;
- `contador -= 1` diminui o valor em 1;
- a tela atualiza automaticamente por causa do `@State`.

---

## 14. Operadores de comparação

Os operadores de comparação são usados para comparar valores.

O resultado de uma comparação sempre será um valor `Bool`, ou seja, `true` ou `false`.

| Operador | Significado | Exemplo |
|---|---|---|
| `==` | Igual a | `idade == 18` |
| `!=` | Diferente de | `nome != "João"` |
| `>` | Maior que | `nota > 7` |
| `<` | Menor que | `idade < 18` |
| `>=` | Maior ou igual | `idade >= 18` |
| `<=` | Menor ou igual | `nota <= 10` |

---

## 15. Igualdade

O operador `==` verifica se dois valores são iguais.

```swift
let senhaDigitada = "1234"
let senhaCorreta = "1234"

print(senhaDigitada == senhaCorreta)
```

Resultado:

```txt
true
```

---

## 16. Diferença

O operador `!=` verifica se dois valores são diferentes.

```swift
let curso = "Design"

print(curso != "Programação")
```

Resultado:

```txt
true
```

---

## 17. Maior e menor

```swift
let idade = 17

print(idade >= 18)
```

Resultado:

```txt
false
```

---

## 18. Operadores de comparação em SwiftUI

Podemos usar comparações para mudar o texto exibido na tela.

```swift
import SwiftUI

struct ContentView: View {
    let idade = 20
    
    var body: some View {
        Text(idade >= 18 ? "Maior de idade" : "Menor de idade")
    }
}
```

Resultado:

```txt
Maior de idade
```

---

## 19. Operadores lógicos

Os operadores lógicos são usados para combinar condições.

| Operador | Nome | Significado |
|---|---|---|
| `&&` | E | Todas as condições precisam ser verdadeiras |
| `||` | OU | Pelo menos uma condição precisa ser verdadeira |
| `!` | NÃO | Inverte o valor lógico |

---

## 20. Operador E: &&

O operador `&&` retorna `true` apenas quando todas as condições são verdadeiras.

```swift
let idade = 20
let temIngresso = true

if idade >= 18 && temIngresso {
    print("Entrada permitida")
} else {
    print("Entrada negada")
}
```

Resultado:

```txt
Entrada permitida
```

---

## 21. Operador OU: ||

O operador `||` retorna `true` quando pelo menos uma condição é verdadeira.

```swift
let temCupom = true
let clientePremium = false

if temCupom || clientePremium {
    print("Desconto aplicado")
} else {
    print("Sem desconto")
}
```

Resultado:

```txt
Desconto aplicado
```

---

## 22. Operador NÃO: !

O operador `!` inverte o valor de uma condição.

```swift
let estaBloqueado = false

if !estaBloqueado {
    print("Acesso permitido")
}
```

Resultado:

```txt
Acesso permitido
```

---

## 23. Operadores lógicos em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    @State private var idade = 18
    @State private var aceitouTermos = false
    
    var podeCadastrar: Bool {
        idade >= 18 && aceitouTermos
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Stepper("Idade: \(idade)", value: $idade, in: 0...100)
            
            Toggle("Aceito os termos", isOn: $aceitouTermos)
            
            Text(podeCadastrar ? "Cadastro permitido" : "Cadastro bloqueado")
            
            Button("Cadastrar") {
                print("Cadastro realizado")
            }
            .disabled(!podeCadastrar)
        }
        .padding()
    }
}
```

Nesse exemplo:

- `idade >= 18` verifica se a pessoa tem 18 anos ou mais;
- `aceitouTermos` verifica se o usuário ativou o `Toggle`;
- `&&` exige que as duas condições sejam verdadeiras;
- `!podeCadastrar` desativa o botão quando o cadastro não é permitido.

---

## 24. Operador ternário

O operador ternário é uma forma curta de escrever uma condição.

Sintaxe:

```swift
condicao ? valorSeVerdadeiro : valorSeFalso
```

Exemplo:

```swift
let nota = 8

let resultado = nota >= 7 ? "Aprovado" : "Reprovado"

print(resultado)
```

Resultado:

```txt
Aprovado
```

---

## 25. Operador ternário em SwiftUI

O operador ternário é muito usado dentro de `Text`.

```swift
import SwiftUI

struct ContentView: View {
    let estaOnline = true
    
    var body: some View {
        Text(estaOnline ? "Online" : "Offline")
    }
}
```

Resultado:

```txt
Online
```

Também pode ser usado para alterar cor, texto ou estado visual.

```swift
import SwiftUI

struct ContentView: View {
    @State private var estaAtivo = false
    
    var body: some View {
        VStack(spacing: 16) {
            Text(estaAtivo ? "Status: Ativo" : "Status: Inativo")
                .foregroundStyle(estaAtivo ? .green : .red)
            
            Button("Alterar status") {
                estaAtivo.toggle()
            }
        }
        .padding()
    }
}
```

---

## 26. Operador de nil coalescing

O operador `??` é usado para definir um valor padrão quando um valor opcional está vazio.

```swift
let nome: String? = nil

let nomeExibido = nome ?? "Nome não informado"

print(nomeExibido)
```

Resultado:

```txt
Nome não informado
```

---

## 27. Nil coalescing em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = nil
    
    var body: some View {
        Text(nome ?? "Visitante")
    }
}
```

Resultado:

```txt
Visitante
```

Agora com valor:

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = "Amanda"
    
    var body: some View {
        Text(nome ?? "Visitante")
    }
}
```

Resultado:

```txt
Amanda
```

---

## 28. Operadores de intervalo

Swift possui operadores para criar intervalos de valores.

| Operador | Nome | Exemplo | Significado |
|---|---|---|---|
| `...` | Intervalo fechado | `1...5` | Vai de 1 até 5 |
| `..<` | Intervalo semiaberto | `1..<5` | Vai de 1 até 4 |

---

## 29. Intervalo fechado

```swift
for numero in 1...5 {
    print(numero)
}
```

Resultado:

```txt
1
2
3
4
5
```

---

## 30. Intervalo semiaberto

```swift
for numero in 1..<5 {
    print(numero)
}
```

Resultado:

```txt
1
2
3
4
```

---

## 31. Operadores de intervalo em SwiftUI

Operadores de intervalo são muito usados em `ForEach`.

```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            ForEach(1...5, id: \.self) { numero in
                Text("Item \(numero)")
            }
        }
    }
}
```

Resultado:

```txt
Item 1
Item 2
Item 3
Item 4
Item 5
```

Também aparecem em componentes como `Stepper` e `Slider`.

```swift
Stepper("Idade: \(idade)", value: $idade, in: 0...100)
```

```swift
Slider(value: $volume, in: 0...100)
```

---

## 32. Exemplo completo

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = "Marina"
    @State private var idade = 18
    @State private var nota = 7.5
    @State private var aceitouTermos = false
    
    var statusIdade: String {
        idade >= 18 ? "Maior de idade" : "Menor de idade"
    }
    
    var statusNota: String {
        nota >= 7 ? "Aprovado" : "Reprovado"
    }
    
    var podeContinuar: Bool {
        idade >= 18 && aceitouTermos
    }
    
    var body: some View {
        VStack(spacing: 20) {
            Text("Operadores em SwiftUI")
                .font(.title2)
                .bold()
            
            Text("Nome: \(nome)")
            
            Stepper("Idade: \(idade)", value: $idade, in: 0...100)
            
            Slider(value: $nota, in: 0...10)
            
            Text("Nota: \(String(format: "%.1f", nota))")
            Text("Status da idade: \(statusIdade)")
            Text("Status da nota: \(statusNota)")
            
            Toggle("Aceito os termos", isOn: $aceitouTermos)
            
            Text(podeContinuar ? "Pode continuar" : "Não pode continuar")
                .foregroundStyle(podeContinuar ? .green : .red)
            
            Button("Continuar") {
                print("Continuando...")
            }
            .disabled(!podeContinuar)
        }
        .padding()
    }
}
```

Resultado inicial esperado:

```txt
Nome: Marina
Idade: 18
Nota: 7.5
Status da idade: Maior de idade
Status da nota: Aprovado
Não pode continuar
```

---

## 33. Principais operadores

| Categoria | Operadores |
|---|---|
| Aritméticos | `+`, `-`, `*`, `/`, `%` |
| Atribuição | `=`, `+=`, `-=`, `*=`, `/=` |
| Comparação | `==`, `!=`, `>`, `<`, `>=`, `<=` |
| Lógicos | `&&`, `||`, `!` |
| Ternário | `? :` |
| Nil coalescing | `??` |
| Intervalo | `...`, `..<` |

---

## Pontos-chave

- Operadores são símbolos usados para realizar operações.
- Operadores aritméticos fazem cálculos matemáticos.
- Operadores de atribuição definem ou atualizam valores.
- Operadores de comparação retornam `true` ou `false`.
- Operadores lógicos combinam condições.
- O operador ternário cria uma condição curta.
- O operador `??` define um valor padrão para valores opcionais.
- Os operadores `...` e `..<` criam intervalos.
- Em SwiftUI, operadores são muito usados com `Text`, `Button`, `Toggle`, `Stepper`, `Slider` e `ForEach`.

---

## Desafio

Crie uma tela em SwiftUI com:

- um `Stepper` para alterar a idade;
- um `Slider` para alterar uma nota;
- um `Toggle` para aceitar os termos;
- um texto dizendo se a pessoa é maior ou menor de idade;
- um texto dizendo se a nota está aprovada ou reprovada;
- um botão que só fique habilitado se a idade for maior ou igual a 18 e os termos estiverem aceitos.

Exemplo esperado:

```txt
Idade: 20
Nota: 8.0
Maior de idade
Aprovado
Pode continuar
```