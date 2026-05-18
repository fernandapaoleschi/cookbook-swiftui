# Tipos de Dados em SwiftUI

Em programação, **tipo de dado** define qual tipo de valor uma variável ou constante pode armazenar.

No Swift, os tipos de dados são muito importantes, porque a linguagem é **fortemente tipada**. Isso significa que cada valor possui um tipo específico, como texto, número inteiro, número decimal ou valor lógico.

No SwiftUI, usamos esses tipos para controlar textos, números, botões, formulários, listas e estados da interface.

---

## 1. O que são tipos de dados?

Tipos de dados indicam qual informação uma variável ou constante pode guardar.

Exemplo:

```swift
let nome: String = "Marina"
let idade: Int = 21
let altura: Double = 1.68
let estaLogado: Bool = true
```

Nesse exemplo:

| Variável | Tipo | Valor |
|---|---|---|
| `nome` | `String` | `"Marina"` |
| `idade` | `Int` | `21` |
| `altura` | `Double` | `1.68` |
| `estaLogado` | `Bool` | `true` |

---

## 2. Inferência de tipo

Em Swift, nem sempre precisamos escrever o tipo da variável.

O próprio Swift consegue identificar o tipo de acordo com o valor atribuído.

```swift
let nome = "João"
let idade = 20
let nota = 8.5
let aprovado = true
```

O Swift entende automaticamente que:

| Valor | Tipo inferido |
|---|---|
| `"João"` | `String` |
| `20` | `Int` |
| `8.5` | `Double` |
| `true` | `Bool` |

Mesmo assim, também é possível declarar o tipo manualmente:

```swift
let nome: String = "João"
let idade: Int = 20
let nota: Double = 8.5
let aprovado: Bool = true
```

---

## 3. String

O tipo `String` representa textos.

Ele pode armazenar nomes, mensagens, títulos, descrições e qualquer conteúdo textual.

```swift
let nome: String = "Bianca"
let mensagem: String = "Bem-vinda ao SwiftUI!"
```

Também podemos usar interpolação de strings para inserir valores dentro de um texto.

```swift
let nome = "Bianca"
let mensagem = "Olá, \(nome)!"

print(mensagem)
```

Resultado:

```txt
Olá, Bianca!
```

---

## 4. String em SwiftUI

No SwiftUI, usamos `String` principalmente com o componente `Text`.

```swift
import SwiftUI

struct ContentView: View {
    let nome = "Bianca"
    
    var body: some View {
        Text("Olá, \(nome)!")
    }
}
```

Resultado exibido na tela:

```txt
Olá, Bianca!
```

---

## 5. Int

O tipo `Int` representa números inteiros.

Ou seja, números sem casas decimais.

```swift
let idade: Int = 22
let quantidade: Int = 5
let episodios: Int = 12
```

Exemplo com cálculo:

```swift
let numero1 = 10
let numero2 = 5

let soma = numero1 + numero2

print(soma)
```

Resultado:

```txt
15
```

---

## 6. Int em SwiftUI

Podemos exibir um `Int` na tela usando interpolação de string.

```swift
import SwiftUI

struct ContentView: View {
    let idade = 22
    
    var body: some View {
        Text("Idade: \(idade)")
    }
}
```

Resultado:

```txt
Idade: 22
```

---

## 7. Double

O tipo `Double` representa números com casas decimais.

```swift
let altura: Double = 1.75
let preco: Double = 29.90
let media: Double = 8.7
```

Exemplo:

```swift
let nota1 = 8.5
let nota2 = 9.0

let media = (nota1 + nota2) / 2

print(media)
```

Resultado:

```txt
8.75
```

---

## 8. Double em SwiftUI

Podemos exibir valores `Double` usando interpolação.

```swift
import SwiftUI

struct ContentView: View {
    let media = 8.75
    
    var body: some View {
        Text("Média final: \(media)")
    }
}
```

Resultado:

```txt
Média final: 8.75
```

Se quiser limitar as casas decimais, podemos usar `String(format:)`.

```swift
import SwiftUI

struct ContentView: View {
    let media = 8.756
    
    var body: some View {
        Text("Média final: \(String(format: "%.2f", media))")
    }
}
```

Resultado:

```txt
Média final: 8.76
```

---

## 9. Bool

O tipo `Bool` representa valores lógicos.

Ele só pode armazenar dois valores:

```swift
true
false
```

Exemplo:

```swift
let estaLogado: Bool = true
let notificacoesAtivas: Bool = false
```

---

## 10. Bool em SwiftUI

No SwiftUI, o tipo `Bool` é muito usado para controlar estados da interface.

Exemplo:

```swift
import SwiftUI

struct ContentView: View {
    let estaLogado = true
    
    var body: some View {
        Text(estaLogado ? "Usuário logado" : "Usuário deslogado")
    }
}
```

Resultado:

```txt
Usuário logado
```

Nesse exemplo, usamos o operador ternário:

```swift
condicao ? valorSeVerdadeiro : valorSeFalso
```

---

## 11. Array

O tipo `Array` representa uma lista de valores.

```swift
let nomes: [String] = ["Marina", "João", "Bianca"]
let idades: [Int] = [18, 20, 22]
```

Também podemos deixar o Swift inferir o tipo:

```swift
let cursos = ["Design", "Programação", "Inovação"]
```

Acessando um item da lista:

```swift
let primeiroCurso = cursos[0]

print(primeiroCurso)
```

Resultado:

```txt
Design
```

---

## 12. Array em SwiftUI

No SwiftUI, arrays são muito usados com `ForEach` para exibir listas de dados.

```swift
import SwiftUI

struct ContentView: View {
    let cursos = ["Design", "Programação", "Inovação"]
    
    var body: some View {
        VStack {
            ForEach(cursos, id: \.self) { curso in
                Text(curso)
            }
        }
    }
}
```

Resultado exibido na tela:

```txt
Design
Programação
Inovação
```

---

## 13. Dictionary

O tipo `Dictionary` armazena dados no formato **chave e valor**.

```swift
let estudante: [String: String] = [
    "nome": "Carlos",
    "curso": "Programação"
]
```

Acessando um valor:

```swift
print(estudante["nome"] ?? "Nome não encontrado")
```

Resultado:

```txt
Carlos
```

O operador `??` serve para definir um valor padrão caso a chave não exista.

---

## 14. Dictionary em SwiftUI

Podemos exibir valores de um dicionário na tela.

```swift
import SwiftUI

struct ContentView: View {
    let estudante = [
        "nome": "Carlos",
        "curso": "Programação"
    ]
    
    var body: some View {
        VStack {
            Text("Nome: \(estudante["nome"] ?? "Não informado")")
            Text("Curso: \(estudante["curso"] ?? "Não informado")")
        }
    }
}
```

Resultado:

```txt
Nome: Carlos
Curso: Programação
```

---

## 15. Optional

Em Swift, uma variável comum não pode receber `nil`.

```swift
var nome: String = nil // Erro
```

Para permitir ausência de valor, usamos um **Optional** com `?`.

```swift
var nome: String? = nil
```

Depois, essa variável pode receber um valor:

```swift
nome = "Amanda"
```

---

## 16. Optional em SwiftUI

Quando usamos valores opcionais no SwiftUI, precisamos tratar o caso em que o valor pode estar vazio.

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = nil
    
    var body: some View {
        Text(nome ?? "Nome não informado")
    }
}
```

Resultado:

```txt
Nome não informado
```

Agora com valor:

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = "Amanda"
    
    var body: some View {
        Text(nome ?? "Nome não informado")
    }
}
```

Resultado:

```txt
Amanda
```

---

## 17. Tuple

Uma `Tuple` permite agrupar valores diferentes em uma única estrutura simples.

```swift
let estudante = (nome: "Lucas", idade: 23, curso: "Design")
```

Acessando os valores:

```swift
print(estudante.nome)
print(estudante.idade)
print(estudante.curso)
```

Resultado:

```txt
Lucas
23
Design
```

---

## 18. Tuple em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let estudante = (nome: "Lucas", idade: 23, curso: "Design")
    
    var body: some View {
        VStack {
            Text("Nome: \(estudante.nome)")
            Text("Idade: \(estudante.idade)")
            Text("Curso: \(estudante.curso)")
        }
    }
}
```

Resultado:

```txt
Nome: Lucas
Idade: 23
Curso: Design
```

---

## 19. Conversão de tipos

Às vezes, precisamos converter um tipo de dado para outro.

Por exemplo, converter `String` para `Int`.

```swift
let idadeTexto = "20"
let idade = Int(idadeTexto)

print(idade ?? 0)
```

Resultado:

```txt
20
```

O resultado de `Int(idadeTexto)` é opcional, porque a conversão pode falhar.

Exemplo de falha:

```swift
let texto = "Swift"
let numero = Int(texto)

print(numero ?? 0)
```

Resultado:

```txt
0
```

---

## 20. Conversão de tipos em SwiftUI

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
            
            Text("Idade digitada: \(idade)")
        }
        .padding()
    }
}
```

Nesse exemplo:

- o `TextField` recebe texto;
- `idadeTexto` é uma `String`;
- a propriedade `idade` tenta converter a `String` para `Int`;
- se a conversão falhar, o valor exibido será `0`.

---

## 21. Type Annotation

Type Annotation é quando escrevemos explicitamente o tipo da variável ou constante.

```swift
let nome: String = "Marina"
let idade: Int = 21
let media: Double = 9.5
let aprovado: Bool = true
```

Essa prática ajuda a deixar o código mais claro em alguns casos.

---

## 22. Type Inference

Type Inference é quando o Swift descobre o tipo automaticamente.

```swift
let nome = "Marina"
let idade = 21
let media = 9.5
let aprovado = true
```

Na maioria dos casos, o Swift consegue entender o tipo sem precisar que ele seja informado manualmente.

---

## 23. Exemplo completo

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = "Marina"
    @State private var idadeTexto = "21"
    @State private var cursoSelecionado = "Programação"
    @State private var notificacoesAtivas = true
    
    let cursos = ["Design", "Programação", "Inovação"]
    
    var idade: Int {
        Int(idadeTexto) ?? 0
    }
    
    var body: some View {
        VStack(spacing: 20) {
            Text("Tipos de Dados")
                .font(.title2)
                .bold()
            
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            TextField("Digite sua idade", text: $idadeTexto)
                .textFieldStyle(.roundedBorder)
                .keyboardType(.numberPad)
            
            Picker("Curso", selection: $cursoSelecionado) {
                ForEach(cursos, id: \.self) { curso in
                    Text(curso)
                }
            }
            .pickerStyle(.menu)
            
            Toggle("Notificações", isOn: $notificacoesAtivas)
            
            VStack(spacing: 8) {
                Text("Nome: \(nome)")
                Text("Idade: \(idade)")
                Text("Curso: \(cursoSelecionado)")
                Text("Notificações: \(notificacoesAtivas ? "Ativas" : "Desativadas")")
            }
        }
        .padding()
    }
}
```

Resultado inicial esperado:

```txt
Nome: Marina
Idade: 21
Curso: Programação
Notificações: Ativas
```

---

## 24. Principais tipos de dados

| Tipo | Significado | Exemplo |
|---|---|---|
| `String` | Texto | `"Marina"` |
| `Int` | Número inteiro | `21` |
| `Double` | Número decimal | `8.5` |
| `Bool` | Verdadeiro ou falso | `true` |
| `Array` | Lista de valores | `["Design", "Programação"]` |
| `Dictionary` | Chave e valor | `["nome": "Carlos"]` |
| `Optional` | Valor que pode ser nulo | `String?` |
| `Tuple` | Agrupamento simples de valores | `(nome: "Lucas", idade: 23)` |

---

## Pontos-chave

- Tipos de dados definem o tipo de valor armazenado.
- Swift é uma linguagem fortemente tipada.
- `String` representa textos.
- `Int` representa números inteiros.
- `Double` representa números decimais.
- `Bool` representa verdadeiro ou falso.
- `Array` representa listas.
- `Dictionary` representa pares de chave e valor.
- `Optional` permite trabalhar com ausência de valor.
- `Tuple` agrupa valores diferentes.
- Swift consegue inferir tipos automaticamente.
- Em SwiftUI, os tipos de dados são usados para controlar textos, estados, formulários e listas.

---

## Desafio

Crie uma tela em SwiftUI com:

- uma variável `String` para o nome;
- uma variável `String` para a idade digitada;
- uma conversão de `String` para `Int`;
- um `Picker` com uma lista de cursos;
- um `Toggle` para indicar se o estudante está ativo;
- textos exibindo todos os dados na tela.

Exemplo esperado:

```txt
Nome: João
Idade: 20
Curso: Design
Status: Ativo
```