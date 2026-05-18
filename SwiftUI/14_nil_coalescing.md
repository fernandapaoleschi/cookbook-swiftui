# Nil Coalescing em SwiftUI

Em Swift, **Nil Coalescing** é uma forma curta e segura de definir um valor padrão quando um optional está vazio.

O operador usado é:

```swift
??
```

Ele é muito útil quando temos uma variável opcional e queremos exibir outro valor caso ela esteja como `nil`.

No SwiftUI, o Nil Coalescing é bastante usado para exibir textos padrão, tratar dados opcionais de API, mostrar imagens alternativas, validar campos e evitar erros com valores ausentes.

---

## 1. O que é Nil Coalescing?

Nil Coalescing é uma forma de dizer:

> “Use este valor se ele existir. Se não existir, use este outro valor.”

Exemplo:

```swift
let nome: String? = nil

let nomeExibido = nome ?? "Visitante"

print(nomeExibido)
```

Resultado:

```txt
Visitante
```

Nesse exemplo:

- `nome` é um optional;
- como `nome` está `nil`, o Swift usa `"Visitante"`;
- o operador `??` define esse valor padrão.

---

## 2. Optional com valor

Quando o optional possui valor, o valor original é usado.

```swift
let nome: String? = "Marina"

let nomeExibido = nome ?? "Visitante"

print(nomeExibido)
```

Resultado:

```txt
Marina
```

Nesse caso, `"Visitante"` não é usado, porque `nome` possui o valor `"Marina"`.

---

## 3. Optional sem valor

Quando o optional está vazio, o valor padrão é usado.

```swift
let nome: String? = nil

let nomeExibido = nome ?? "Visitante"

print(nomeExibido)
```

Resultado:

```txt
Visitante
```

---

## 4. Sintaxe do Nil Coalescing

A sintaxe é:

```swift
optional ?? valorPadrao
```

Exemplo:

```swift
let email: String? = nil

let emailExibido = email ?? "Email não informado"
```

Nesse exemplo:

- se `email` tiver valor, esse valor será usado;
- se `email` for `nil`, será usado `"Email não informado"`.

---

## 5. Nil Coalescing com String

```swift
let nome: String? = nil

print(nome ?? "Nome não informado")
```

Resultado:

```txt
Nome não informado
```

Agora com valor:

```swift
let nome: String? = "Carlos"

print(nome ?? "Nome não informado")
```

Resultado:

```txt
Carlos
```

---

## 6. Nil Coalescing com Int

Também podemos usar `??` com números inteiros.

```swift
let idade: Int? = nil

let idadeExibida = idade ?? 0

print(idadeExibida)
```

Resultado:

```txt
0
```

Agora com valor:

```swift
let idade: Int? = 22

let idadeExibida = idade ?? 0

print(idadeExibida)
```

Resultado:

```txt
22
```

---

## 7. Nil Coalescing com Double

```swift
let preco: Double? = nil

let precoFinal = preco ?? 0.0

print(precoFinal)
```

Resultado:

```txt
0.0
```

Agora com valor:

```swift
let preco: Double? = 149.90

let precoFinal = preco ?? 0.0

print(precoFinal)
```

Resultado:

```txt
149.9
```

---

## 8. Nil Coalescing com Bool

```swift
let notificacoesAtivas: Bool? = nil

let status = notificacoesAtivas ?? false

print(status)
```

Resultado:

```txt
false
```

Nesse exemplo, se o valor não existir, consideramos `false` como padrão.

---

## 9. Nil Coalescing em SwiftUI

No SwiftUI, podemos usar `??` diretamente dentro de um `Text`.

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = nil
    
    var body: some View {
        Text("Olá, \(nome ?? "Visitante")!")
    }
}
```

Resultado exibido na tela:

```txt
Olá, Visitante!
```

Agora com valor:

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = "Amanda"
    
    var body: some View {
        Text("Olá, \(nome ?? "Visitante")!")
    }
}
```

Resultado:

```txt
Olá, Amanda!
```

---

## 10. Nil Coalescing com dados de usuário

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = "João"
    let email: String? = nil
    
    var body: some View {
        VStack(alignment: .leading, spacing: 8) {
            Text("Nome: \(nome ?? "Nome não informado")")
            Text("Email: \(email ?? "Email não informado")")
        }
        .padding()
    }
}
```

Resultado:

```txt
Nome: João
Email: Email não informado
```

---

## 11. Nil Coalescing com Struct

Optionals são muito comuns dentro de structs.

```swift
struct Estudante {
    let nome: String
    let email: String?
}
```

Exemplo usando `??`:

```swift
let estudante = Estudante(nome: "Bianca", email: nil)

print(estudante.email ?? "Email não informado")
```

Resultado:

```txt
Email não informado
```

---

## 12. Struct com Nil Coalescing em SwiftUI

```swift
import SwiftUI

struct Estudante {
    let nome: String
    let email: String?
    let telefone: String?
}

struct ContentView: View {
    let estudante = Estudante(
        nome: "Bianca",
        email: nil,
        telefone: "81999990000"
    )
    
    var body: some View {
        VStack(alignment: .leading, spacing: 8) {
            Text("Nome: \(estudante.nome)")
            Text("Email: \(estudante.email ?? "Não informado")")
            Text("Telefone: \(estudante.telefone ?? "Não informado")")
        }
        .padding()
    }
}
```

Resultado:

```txt
Nome: Bianca
Email: Não informado
Telefone: 81999990000
```

---

## 13. Nil Coalescing em lista de structs

```swift
import SwiftUI

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
    let email: String?
}

struct ContentView: View {
    let estudantes = [
        Estudante(nome: "Marina", email: "marina@email.com"),
        Estudante(nome: "João", email: nil),
        Estudante(nome: "Carlos", email: "carlos@email.com")
    ]
    
    var body: some View {
        List(estudantes) { estudante in
            VStack(alignment: .leading) {
                Text(estudante.nome)
                    .font(.headline)
                
                Text(estudante.email ?? "Email não informado")
                    .font(.subheadline)
            }
        }
    }
}
```

Nesse exemplo:

- alguns estudantes possuem email;
- outros estão com `email` como `nil`;
- o operador `??` evita que a tela fique sem informação.

---

## 14. Nil Coalescing com conversão de String para Int

Quando convertemos uma `String` para `Int`, o resultado pode ser `nil`.

```swift
let idadeTexto = "20"

let idade = Int(idadeTexto) ?? 0

print(idade)
```

Resultado:

```txt
20
```

Agora com valor inválido:

```swift
let idadeTexto = "Swift"

let idade = Int(idadeTexto) ?? 0

print(idade)
```

Resultado:

```txt
0
```

Nesse caso, `"Swift"` não pode virar número, então o Swift usa o valor padrão `0`.

---

## 15. Conversão em SwiftUI com Nil Coalescing

```swift
import SwiftUI

struct ContentView: View {
    @State private var idadeTexto = ""
    
    var idade: Int {
        Int(idadeTexto) ?? 0
    }
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite sua idade", text: $idadeTexto)
                .textFieldStyle(.roundedBorder)
                .keyboardType(.numberPad)
            
            Text("Idade: \(idade)")
        }
        .padding()
    }
}
```

Nesse exemplo:

- `idadeTexto` é uma `String`;
- `Int(idadeTexto)` tenta converter para número;
- se a conversão falhar, o valor será `0`.

---

## 16. Nil Coalescing com Double em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    @State private var precoTexto = ""
    
    var preco: Double {
        Double(precoTexto) ?? 0.0
    }
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite o preço", text: $precoTexto)
                .textFieldStyle(.roundedBorder)
                .keyboardType(.decimalPad)
            
            Text("Preço: R$ \(String(format: "%.2f", preco))")
        }
        .padding()
    }
}
```

Nesse exemplo:

- o usuário digita o preço como texto;
- o Swift tenta converter para `Double`;
- se não conseguir, usa `0.0`.

---

## 17. Nil Coalescing com Optional Chaining

Podemos combinar optional chaining `?.` com nil coalescing `??`.

```swift
let nome: String? = "marina"

let nomeFormatado = nome?.uppercased() ?? "NOME NÃO INFORMADO"

print(nomeFormatado)
```

Resultado:

```txt
MARINA
```

Agora com `nil`:

```swift
let nome: String? = nil

let nomeFormatado = nome?.uppercased() ?? "NOME NÃO INFORMADO"

print(nomeFormatado)
```

Resultado:

```txt
NOME NÃO INFORMADO
```

Nesse exemplo:

- `nome?.uppercased()` tenta transformar o texto em maiúsculo;
- se `nome` for `nil`, o resultado final será `"NOME NÃO INFORMADO"`.

---

## 18. Optional Chaining com SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = "marina"
    
    var body: some View {
        Text(nome?.uppercased() ?? "NOME NÃO INFORMADO")
    }
}
```

Resultado:

```txt
MARINA
```

---

## 19. Nil Coalescing com imagem

Quando usamos URL de imagem, o endereço pode não existir.

```swift
let imagemURL: String? = nil

let urlPadrao = "https://picsum.photos/200"

let enderecoFinal = imagemURL ?? urlPadrao

print(enderecoFinal)
```

Resultado:

```txt
https://picsum.photos/200
```

---

## 20. Nil Coalescing com AsyncImage

```swift
import SwiftUI

struct ContentView: View {
    let imagemURL: String? = nil
    
    var enderecoFinal: String {
        imagemURL ?? "https://picsum.photos/200"
    }
    
    var body: some View {
        VStack(spacing: 16) {
            if let url = URL(string: enderecoFinal) {
                AsyncImage(url: url) { image in
                    image
                        .resizable()
                        .scaledToFit()
                } placeholder: {
                    ProgressView()
                }
                .frame(width: 200, height: 200)
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- `imagemURL` está como `nil`;
- `enderecoFinal` usa uma imagem padrão;
- `AsyncImage` carrega a URL final.

---

## 21. Nil Coalescing x If Let

O `??` e o `if let` trabalham com optionals, mas são usados em situações diferentes.

| Estrutura | Melhor uso |
|---|---|
| `??` | Quando queremos apenas um valor padrão |
| `if let` | Quando precisamos executar uma lógica maior |

Exemplo com `??`:

```swift
Text(nome ?? "Visitante")
```

Exemplo com `if let`:

```swift
if let nome {
    Text("Olá, \(nome)")
} else {
    Text("Visitante")
}
```

Use `??` quando a substituição for simples.

Use `if let` quando precisar de mais validações ou componentes diferentes.

---

## 22. Nil Coalescing x Guard Let

O `guard let` é melhor quando estamos dentro de uma função e queremos parar a execução caso o valor não exista.

Com `??`:

```swift
let nomeExibido = nome ?? "Visitante"
```

Com `guard let`:

```swift
func confirmar(nome: String?) {
    guard let nome else {
        print("Nome não informado")
        return
    }
    
    print("Confirmado: \(nome)")
}
```

Use `??` para valor padrão.

Use `guard let` para validar e interromper uma função.

---

## 23. Cuidado com valores padrão

O Nil Coalescing é útil, mas o valor padrão precisa fazer sentido.

Exemplo:

```swift
let idade = Int("abc") ?? 0
```

Nesse caso, `0` pode esconder um erro de digitação.

Às vezes, é melhor usar `if let` para mostrar uma mensagem:

```swift
if let idade = Int("abc") {
    print("Idade: \(idade)")
} else {
    print("Idade inválida")
}
```

Use `??` quando um valor padrão for realmente aceitável.

---

## 24. Exemplo completo

```swift
import SwiftUI

struct Produto: Identifiable {
    let id = UUID()
    let nome: String
    let precoTexto: String
    let categoria: String?
    let imagemURL: String?
}

struct ContentView: View {
    @State private var produtos = [
        Produto(
            nome: "Teclado",
            precoTexto: "150.00",
            categoria: "Eletrônicos",
            imagemURL: "https://picsum.photos/200"
        ),
        Produto(
            nome: "Mouse",
            precoTexto: "Swift",
            categoria: nil,
            imagemURL: nil
        ),
        Produto(
            nome: "Caderno",
            precoTexto: "25.00",
            categoria: "Papelaria",
            imagemURL: nil
        )
    ]
    
    var body: some View {
        NavigationStack {
            List(produtos) { produto in
                VStack(alignment: .leading, spacing: 8) {
                    Text(produto.nome)
                        .font(.headline)
                    
                    Text("Categoria: \(produto.categoria ?? "Sem categoria")")
                    
                    Text("Preço: R$ \(String(format: "%.2f", Double(produto.precoTexto) ?? 0.0))")
                    
                    Text("Imagem: \(produto.imagemURL ?? "Imagem não disponível")")
                        .font(.caption)
                }
            }
            .navigationTitle("Nil Coalescing")
        }
    }
}
```

Nesse exemplo:

- `categoria` é opcional;
- `imagemURL` é opcional;
- `Double(produto.precoTexto)` pode retornar `nil`;
- `??` define valores padrão para todos esses casos.

---

## 25. Resumo do Nil Coalescing

| Conceito | Exemplo | Significado |
|---|---|---|
| Nil Coalescing | `nome ?? "Visitante"` | Usa valor padrão se for `nil` |
| Optional String | `email ?? "Não informado"` | Texto padrão |
| Optional Int | `idade ?? 0` | Número padrão |
| Conversão | `Int(texto) ?? 0` | Número padrão se conversão falhar |
| Optional chaining | `nome?.uppercased() ?? "Sem nome"` | Acessa e define valor padrão |
| SwiftUI | `Text(nome ?? "Visitante")` | Exibe dado opcional com segurança |

---

## Pontos-chave

- Nil Coalescing usa o operador `??`.
- Ele define um valor padrão quando um optional é `nil`.
- Se o optional tiver valor, esse valor será usado.
- Se o optional for `nil`, o valor depois do `??` será usado.
- É uma forma curta de tratar optionals.
- É muito usado em `Text`, listas, structs, dados de API e conversões.
- Pode ser combinado com optional chaining `?.`.
- Use `??` quando um valor padrão simples fizer sentido.
- Use `if let` ou `guard let` quando precisar de validações maiores.

---

## Desafio

Crie uma tela em SwiftUI com:

- uma struct chamada `Aluno`;
- os campos `nome`, `email`, `curso` e `notaTexto`;
- `email` e `curso` devem ser opcionais;
- uma lista de alunos;
- exibição de `"Email não informado"` quando o email for `nil`;
- exibição de `"Curso não informado"` quando o curso for `nil`;
- conversão de `notaTexto` para `Double`;
- uso de `0.0` como valor padrão quando a nota for inválida.

Exemplo esperado:

```txt
Aluno: Marina
Email: marina@email.com
Curso: Design
Nota: 8.5

Aluno: João
Email não informado
Curso não informado
Nota: 0.0
```