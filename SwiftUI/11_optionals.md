# Optionals em SwiftUI

Em Swift, **Optional** é um tipo que representa um valor que pode existir ou não.

Ou seja, uma variável opcional pode ter um valor ou pode estar vazia com `nil`.

No SwiftUI, optionals aparecem bastante quando trabalhamos com formulários, dados de API, imagens, usuários, listas, navegação e valores que podem não estar disponíveis no momento.

---

## 1. O que é Optional?

Um Optional é usado quando uma variável pode não ter valor.

Exemplo comum:

```swift
var nome: String? = nil
```

Nesse exemplo:

- `nome` é do tipo `String?`;
- o `?` indica que essa variável é opcional;
- ela pode guardar uma `String`;
- ou pode estar vazia com `nil`.

---

## 2. Variável comum não aceita nil

Em Swift, uma variável comum não pode receber `nil`.

```swift
var nome: String = nil // Erro
```

Isso acontece porque `String` significa que a variável precisa ter obrigatoriamente um texto.

Para permitir ausência de valor, usamos `String?`.

```swift
var nome: String? = nil
```

---

## 3. Declarando Optionals

Podemos criar optionals com vários tipos.

```swift
var nome: String? = nil
var idade: Int? = nil
var altura: Double? = nil
var estaAtivo: Bool? = nil
```

Depois, esses valores podem receber dados normalmente.

```swift
nome = "Marina"
idade = 21
altura = 1.68
estaAtivo = true
```

---

## 4. Optional com valor

```swift
var nome: String? = "João"

print(nome)
```

Resultado:

```txt
Optional("João")
```

O Swift mostra `Optional("João")` porque o valor ainda está embrulhado dentro do optional.

Para usar o valor real, precisamos desembrulhar o optional.

---

## 5. Optional sem valor

```swift
var nome: String? = nil

print(nome)
```

Resultado:

```txt
nil
```

Nesse caso, a variável não possui valor.

---

## 6. Nil

`nil` representa ausência de valor.

```swift
var usuario: String? = nil
```

Isso significa que `usuario` ainda não possui nenhum valor.

Depois, podemos atribuir um valor:

```swift
usuario = "Amanda"
```

---

## 7. Por que Optionals existem?

Optionals ajudam o Swift a evitar erros comuns.

Em vez de o programa tentar usar um valor inexistente e quebrar, o Swift obriga a gente a tratar a possibilidade de `nil`.

Exemplo:

```swift
var nome: String? = nil
```

Antes de exibir ou manipular `nome`, precisamos verificar se existe um valor.

---

## 8. Optional Binding com if let

Uma das formas mais comuns de desembrulhar um optional é usando `if let`.

```swift
var nome: String? = "Bianca"

if let nomeDesembrulhado = nome {
    print("Nome: \(nomeDesembrulhado)")
} else {
    print("Nome não informado")
}
```

Resultado:

```txt
Nome: Bianca
```

Nesse exemplo:

- se `nome` tiver valor, ele será colocado em `nomeDesembrulhado`;
- se `nome` for `nil`, o bloco do `else` será executado.

---

## 9. if let com nil

```swift
var nome: String? = nil

if let nomeDesembrulhado = nome {
    print("Nome: \(nomeDesembrulhado)")
} else {
    print("Nome não informado")
}
```

Resultado:

```txt
Nome não informado
```

Como `nome` está vazio, o código entra no `else`.

---

## 10. if let simplificado

Em versões mais recentes do Swift, podemos usar uma forma mais curta.

```swift
var nome: String? = "Carlos"

if let nome {
    print("Nome: \(nome)")
} else {
    print("Nome não informado")
}
```

Resultado:

```txt
Nome: Carlos
```

Nesse exemplo, o Swift desembrulha `nome` usando o mesmo nome da variável.

---

## 11. Optionals em SwiftUI com if let

No SwiftUI, podemos usar `if let` para exibir uma informação apenas quando ela existe.

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = "Marina"
    
    var body: some View {
        VStack {
            if let nome {
                Text("Olá, \(nome)!")
            } else {
                Text("Nome não informado")
            }
        }
    }
}
```

Resultado:

```txt
Olá, Marina!
```

---

## 12. Optional sem valor em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = nil
    
    var body: some View {
        VStack {
            if let nome {
                Text("Olá, \(nome)!")
            } else {
                Text("Nome não informado")
            }
        }
    }
}
```

Resultado:

```txt
Nome não informado
```

---

## 13. Nil Coalescing Operator

O operador `??` define um valor padrão caso o optional seja `nil`.

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

- se `nome` tiver valor, esse valor será usado;
- se `nome` for `nil`, será usado `"Visitante"`.

---

## 14. Nil Coalescing em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = nil
    
    var body: some View {
        Text("Olá, \(nome ?? "Visitante")!")
    }
}
```

Resultado:

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

## 15. Optional Chaining

Optional chaining permite acessar propriedades ou métodos de um optional sem precisar desembrulhar manualmente.

Usamos `?.`.

```swift
let nome: String? = "Marina"

print(nome?.uppercased())
```

Resultado:

```txt
Optional("MARINA")
```

Se `nome` for `nil`, nada quebra.

```swift
let nome: String? = nil

print(nome?.uppercased())
```

Resultado:

```txt
nil
```

---

## 16. Optional Chaining com valor padrão

Podemos combinar `?.` com `??`.

```swift
let nome: String? = "Marina"

let nomeMaiusculo = nome?.uppercased() ?? "NOME NÃO INFORMADO"

print(nomeMaiusculo)
```

Resultado:

```txt
MARINA
```

Agora com `nil`:

```swift
let nome: String? = nil

let nomeMaiusculo = nome?.uppercased() ?? "NOME NÃO INFORMADO"

print(nomeMaiusculo)
```

Resultado:

```txt
NOME NÃO INFORMADO
```

---

## 17. Optional Chaining em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = "Bianca"
    
    var body: some View {
        Text(nome?.uppercased() ?? "NOME NÃO INFORMADO")
    }
}
```

Resultado:

```txt
BIANCA
```

---

## 18. Force Unwrap

O force unwrap usa `!` para forçar a retirada do valor de um optional.

```swift
let nome: String? = "Carlos"

print(nome!)
```

Resultado:

```txt
Carlos
```

Porém, isso é perigoso.

Se o optional estiver `nil`, o aplicativo pode quebrar.

```swift
let nome: String? = nil

print(nome!) // Erro em tempo de execução
```

Por isso, evite usar `!` quando não tiver certeza absoluta de que existe um valor.

---

## 19. Forma segura x forma perigosa

Forma perigosa:

```swift
let nome: String? = nil

Text(nome!) // Pode quebrar o app
```

Forma segura:

```swift
let nome: String? = nil

Text(nome ?? "Visitante")
```

Ou:

```swift
if let nome {
    Text(nome)
} else {
    Text("Visitante")
}
```

---

## 20. Guard let

O `guard let` é muito usado dentro de funções para validar se um optional possui valor antes de continuar.

```swift
func exibirNome(_ nome: String?) {
    guard let nome else {
        print("Nome não informado")
        return
    }
    
    print("Nome: \(nome)")
}

exibirNome(nil)
exibirNome("João")
```

Resultado:

```txt
Nome não informado
Nome: João
```

Nesse exemplo:

- se `nome` for `nil`, a função para no `return`;
- se `nome` tiver valor, o código continua normalmente.

---

## 21. Guard let em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome: String? = nil
    @State private var mensagem = ""
    
    func confirmar() {
        guard let nome else {
            mensagem = "Digite um nome antes de continuar"
            return
        }
        
        mensagem = "Cadastro confirmado para \(nome)"
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Button("Definir nome") {
                nome = "Marina"
            }
            
            Button("Confirmar") {
                confirmar()
            }
            
            Text(mensagem)
        }
        .padding()
    }
}
```

Nesse exemplo:

- `nome` começa como `nil`;
- ao clicar em `"Definir nome"`, `nome` recebe `"Marina"`;
- ao clicar em `"Confirmar"`, a função verifica se existe um nome.

---

## 22. Optionals com TextField

O `TextField` trabalha melhor com `String` comum, não com `String?`.

Por isso, quando o usuário digita um texto, geralmente usamos:

```swift
@State private var nome = ""
```

Em vez de:

```swift
@State private var nome: String? = nil
```

Exemplo recomendado:

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Text(nome.isEmpty ? "Nome não informado" : "Olá, \(nome)!")
        }
        .padding()
    }
}
```

Nesse exemplo, usamos string vazia `""` para representar campo sem preenchimento.

---

## 23. Convertendo String para Int

Quando convertemos uma `String` para `Int`, o resultado é um optional.

```swift
let idadeTexto = "20"

let idade = Int(idadeTexto)

print(idade)
```

Resultado:

```txt
Optional(20)
```

Isso acontece porque a conversão pode falhar.

---

## 24. Conversão que falha

```swift
let idadeTexto = "Swift"

let idade = Int(idadeTexto)

print(idade)
```

Resultado:

```txt
nil
```

Como `"Swift"` não pode virar número, o resultado é `nil`.

---

## 25. Tratando conversão com nil coalescing

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

---

## 26. Conversão em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    @State private var idadeTexto = ""
    
    var idade: Int? {
        Int(idadeTexto)
    }
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite sua idade", text: $idadeTexto)
                .textFieldStyle(.roundedBorder)
                .keyboardType(.numberPad)
            
            if let idade {
                Text("Idade: \(idade)")
            } else {
                Text("Digite uma idade válida")
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- `idadeTexto` é uma `String`;
- `idade` tenta converter o texto para `Int`;
- se a conversão funcionar, mostra a idade;
- se falhar, mostra uma mensagem.

---

## 27. Optional com Struct

Optionals são muito comuns dentro de structs.

```swift
struct Estudante {
    let nome: String
    let email: String?
}
```

Nesse exemplo, `nome` é obrigatório, mas `email` é opcional.

Criando estudantes:

```swift
let estudante1 = Estudante(nome: "Marina", email: "marina@email.com")
let estudante2 = Estudante(nome: "João", email: nil)
```

---

## 28. Optional com Struct em SwiftUI

```swift
import SwiftUI

struct Estudante {
    let nome: String
    let email: String?
}

struct ContentView: View {
    let estudante = Estudante(nome: "João", email: nil)
    
    var body: some View {
        VStack(alignment: .leading, spacing: 8) {
            Text("Nome: \(estudante.nome)")
            Text("Email: \(estudante.email ?? "Não informado")")
        }
        .padding()
    }
}
```

Resultado:

```txt
Nome: João
Email: Não informado
```

---

## 29. Optional em lista de structs

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
        Estudante(nome: "Bianca", email: "bianca@email.com")
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

- alguns estudantes têm email;
- outros não;
- o `??` garante que a tela sempre tenha algo para exibir.

---

## 30. Optional com imagem

Quando carregamos imagens por URL, a URL pode ser inválida.

Por isso, `URL(string:)` retorna um optional.

```swift
let endereco = "https://example.com/imagem.png"

let url = URL(string: endereco)
```

O tipo de `url` é:

```swift
URL?
```

---

## 31. Optional com AsyncImage

```swift
import SwiftUI

struct ContentView: View {
    let enderecoImagem: String? = "https://picsum.photos/200"
    
    var body: some View {
        VStack(spacing: 16) {
            if let enderecoImagem,
               let url = URL(string: enderecoImagem) {
                AsyncImage(url: url) { image in
                    image
                        .resizable()
                        .scaledToFit()
                } placeholder: {
                    ProgressView()
                }
                .frame(width: 200, height: 200)
            } else {
                Text("Imagem não disponível")
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- `enderecoImagem` é opcional;
- `URL(string:)` também retorna optional;
- usamos `if let` para verificar os dois valores antes de carregar a imagem.

---

## 32. Optional com estado selecionado

Em SwiftUI, optionals são muito usados para guardar um item selecionado.

```swift
import SwiftUI

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
}

struct ContentView: View {
    let estudantes = [
        Estudante(nome: "Marina"),
        Estudante(nome: "João"),
        Estudante(nome: "Bianca")
    ]
    
    @State private var estudanteSelecionado: Estudante? = nil
    
    var body: some View {
        VStack(spacing: 16) {
            ForEach(estudantes) { estudante in
                Button(estudante.nome) {
                    estudanteSelecionado = estudante
                }
            }
            
            if let estudanteSelecionado {
                Text("Selecionado: \(estudanteSelecionado.nome)")
            } else {
                Text("Nenhum estudante selecionado")
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- `estudanteSelecionado` começa como `nil`;
- ao clicar em um botão, ele recebe um estudante;
- a tela exibe o nome selecionado.

---

## 33. Exemplo completo

```swift
import SwiftUI

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
    let idadeTexto: String
    let email: String?
}

struct ContentView: View {
    @State private var estudantes = [
        Estudante(nome: "Marina", idadeTexto: "21", email: "marina@email.com"),
        Estudante(nome: "João", idadeTexto: "Swift", email: nil),
        Estudante(nome: "Bianca", idadeTexto: "19", email: "bianca@email.com")
    ]
    
    @State private var estudanteSelecionado: Estudante? = nil
    @State private var mensagem = ""
    
    func idadeConvertida(_ idadeTexto: String) -> Int? {
        return Int(idadeTexto)
    }
    
    func confirmarSelecao() {
        guard let estudanteSelecionado else {
            mensagem = "Selecione um estudante antes de continuar"
            return
        }
        
        mensagem = "Estudante selecionado: \(estudanteSelecionado.nome)"
    }
    
    var body: some View {
        NavigationStack {
            VStack(spacing: 16) {
                List(estudantes) { estudante in
                    Button {
                        estudanteSelecionado = estudante
                    } label: {
                        VStack(alignment: .leading, spacing: 6) {
                            Text(estudante.nome)
                                .font(.headline)
                            
                            Text("Email: \(estudante.email ?? "Não informado")")
                            
                            if let idade = idadeConvertida(estudante.idadeTexto) {
                                Text("Idade: \(idade)")
                            } else {
                                Text("Idade inválida")
                            }
                        }
                    }
                }
                
                if let estudanteSelecionado {
                    Text("Selecionado: \(estudanteSelecionado.nome)")
                } else {
                    Text("Nenhum estudante selecionado")
                }
                
                Button("Confirmar seleção") {
                    confirmarSelecao()
                }
                
                Text(mensagem)
                    .multilineTextAlignment(.center)
            }
            .navigationTitle("Optionals")
        }
    }
}
```

Nesse exemplo:

- `email` é opcional;
- `estudanteSelecionado` também é opcional;
- `idadeConvertida` retorna `Int?`;
- `guard let` valida se existe estudante selecionado;
- `if let` trata valores antes de exibir;
- `??` define texto padrão para email ausente.

---

## 34. Resumo dos Optionals

| Conceito | Exemplo | Uso |
|---|---|---|
| Optional | `String?` | Valor pode existir ou ser `nil` |
| Nil | `nil` | Ausência de valor |
| if let | `if let nome { ... }` | Desembrulha com segurança |
| guard let | `guard let nome else { return }` | Valida antes de continuar |
| Nil coalescing | `nome ?? "Visitante"` | Define valor padrão |
| Optional chaining | `nome?.uppercased()` | Acessa valor opcional com segurança |
| Force unwrap | `nome!` | Força o uso do valor |

---

## Pontos-chave

- Optional representa um valor que pode existir ou não.
- Para criar um optional, usamos `?`.
- `nil` representa ausência de valor.
- Variáveis comuns não podem receber `nil`.
- `if let` desembrulha um optional com segurança.
- `guard let` é usado para validar optionals dentro de funções.
- `??` define um valor padrão quando o optional está vazio.
- `?.` permite acessar propriedades ou métodos de forma segura.
- `!` força o uso do valor, mas pode quebrar o app se o valor for `nil`.
- Em SwiftUI, optionals aparecem em dados de API, imagens, seleção de itens, formulários e conversões de tipos.

---

## Desafio

Crie uma tela em SwiftUI com:

- uma struct chamada `Produto`;
- os campos `nome`, `precoTexto` e `imagemURL`;
- `imagemURL` deve ser opcional;
- uma função que converta `precoTexto` para `Double?`;
- uma lista de produtos;
- exibição de `"Imagem não disponível"` quando a URL for `nil`;
- exibição de `"Preço inválido"` quando a conversão falhar;
- um estado opcional para guardar o produto selecionado.

Exemplo esperado:

```txt
Produto: Teclado
Preço: R$ 150.00
Imagem disponível

Produto: Mouse
Preço inválido
Imagem não disponível

Selecionado: Teclado
```