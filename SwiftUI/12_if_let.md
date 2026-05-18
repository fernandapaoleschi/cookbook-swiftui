# If Let em SwiftUI

Em Swift, `if let` é uma estrutura usada para trabalhar com **optionals** de forma segura.

Um optional é um valor que pode existir ou pode estar vazio com `nil`.

O `if let` verifica se o optional possui valor. Se possuir, ele desembrulha esse valor e permite usá-lo dentro do bloco.

No SwiftUI, `if let` é muito usado para exibir dados opcionais, tratar respostas de API, carregar imagens, mostrar informações selecionadas e evitar erros com valores `nil`.

---

## 1. O que é if let?

O `if let` é usado para verificar se um optional tem valor.

Exemplo:

```swift
var nome: String? = "Marina"

if let nomeDesembrulhado = nome {
    print("Nome: \(nomeDesembrulhado)")
} else {
    print("Nome não informado")
}
```

Resultado:

```txt
Nome: Marina
```

Nesse exemplo:

- `nome` é um optional;
- `if let` verifica se `nome` possui valor;
- se possuir, o valor é colocado em `nomeDesembrulhado`;
- se for `nil`, o código entra no `else`.

---

## 2. Optional com nil

Quando o optional está vazio, o bloco do `else` é executado.

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

---

## 3. Por que usar if let?

Não podemos usar um optional diretamente como se ele sempre tivesse valor.

```swift
var nome: String? = "João"

print(nome.uppercased()) // Erro
```

Esse código gera erro porque `nome` é uma `String?`, não uma `String`.

Para acessar o valor com segurança, usamos `if let`.

```swift
var nome: String? = "João"

if let nomeDesembrulhado = nome {
    print(nomeDesembrulhado.uppercased())
}
```

Resultado:

```txt
JOÃO
```

---

## 4. If let simplificado

Em versões mais recentes do Swift, podemos usar uma forma mais curta do `if let`.

Forma tradicional:

```swift
var nome: String? = "Bianca"

if let nomeDesembrulhado = nome {
    print("Nome: \(nomeDesembrulhado)")
}
```

Forma simplificada:

```swift
var nome: String? = "Bianca"

if let nome {
    print("Nome: \(nome)")
}
```

Resultado:

```txt
Nome: Bianca
```

Nessa forma, o Swift desembrulha o optional usando o mesmo nome da variável.

---

## 5. If let com else

Podemos usar `else` para tratar o caso em que o valor é `nil`.

```swift
var email: String? = nil

if let email {
    print("Email: \(email)")
} else {
    print("Email não informado")
}
```

Resultado:

```txt
Email não informado
```

---

## 6. If let com múltiplos optionals

Também é possível desembrulhar mais de um optional no mesmo `if let`.

```swift
let nome: String? = "Carlos"
let email: String? = "carlos@email.com"

if let nome, let email {
    print("Nome: \(nome)")
    print("Email: \(email)")
} else {
    print("Dados incompletos")
}
```

Resultado:

```txt
Nome: Carlos
Email: carlos@email.com
```

Nesse exemplo, o bloco só executa se `nome` e `email` tiverem valor.

---

## 7. If let com condição extra

Podemos combinar `if let` com uma condição.

```swift
let idadeTexto: String? = "20"

if let idadeTexto,
   let idade = Int(idadeTexto),
   idade >= 18 {
    print("Maior de idade")
} else {
    print("Idade inválida ou menor de idade")
}
```

Resultado:

```txt
Maior de idade
```

Nesse exemplo:

- primeiro verificamos se `idadeTexto` existe;
- depois tentamos converter para `Int`;
- por fim, verificamos se `idade >= 18`.

---

## 8. If let em SwiftUI

No SwiftUI, `if let` pode ser usado dentro do `body`.

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

Resultado exibido na tela:

```txt
Olá, Marina!
```

---

## 9. If let em SwiftUI com nil

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

## 10. If let com TextField

Normalmente, o `TextField` trabalha melhor com `String` comum.

Mas podemos transformar o texto digitado em optional quando precisamos validar.

```swift
import SwiftUI

struct ContentView: View {
    @State private var nomeDigitado = ""
    
    var nomeValido: String? {
        let nomeTratado = nomeDigitado.trimmingCharacters(in: .whitespaces)
        return nomeTratado.isEmpty ? nil : nomeTratado
    }
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite seu nome", text: $nomeDigitado)
                .textFieldStyle(.roundedBorder)
            
            if let nomeValido {
                Text("Olá, \(nomeValido)!")
                    .foregroundStyle(.green)
            } else {
                Text("Digite um nome válido")
                    .foregroundStyle(.red)
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- `nomeDigitado` recebe o texto do campo;
- `nomeValido` retorna `nil` se o campo estiver vazio;
- `if let` exibe uma mensagem diferente conforme o valor.

---

## 11. If let com conversão de String para Int

Quando convertemos uma `String` para `Int`, o resultado é opcional.

```swift
let idadeTexto = "20"
let idade = Int(idadeTexto)

print(idade)
```

Resultado:

```txt
Optional(20)
```

Para usar o valor convertido, podemos aplicar `if let`.

```swift
let idadeTexto = "20"

if let idade = Int(idadeTexto) {
    print("Idade: \(idade)")
} else {
    print("Idade inválida")
}
```

Resultado:

```txt
Idade: 20
```

---

## 12. If let com conversão inválida

```swift
let idadeTexto = "Swift"

if let idade = Int(idadeTexto) {
    print("Idade: \(idade)")
} else {
    print("Idade inválida")
}
```

Resultado:

```txt
Idade inválida
```

Como `"Swift"` não pode ser convertido para número, o resultado de `Int(idadeTexto)` é `nil`.

---

## 13. If let com conversão em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    @State private var idadeTexto = ""
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite sua idade", text: $idadeTexto)
                .textFieldStyle(.roundedBorder)
                .keyboardType(.numberPad)
            
            if let idade = Int(idadeTexto) {
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

- o usuário digita uma idade;
- o Swift tenta converter o texto para `Int`;
- se conseguir, mostra a idade;
- se não conseguir, mostra uma mensagem de aviso.

---

## 14. If let com Struct

Optionals são muito usados dentro de structs.

```swift
struct Estudante {
    let nome: String
    let email: String?
}
```

Nesse exemplo, `email` pode existir ou não.

```swift
let estudante = Estudante(nome: "Amanda", email: "amanda@email.com")

if let email = estudante.email {
    print("Email: \(email)")
} else {
    print("Email não informado")
}
```

Resultado:

```txt
Email: amanda@email.com
```

---

## 15. If let com Struct em SwiftUI

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
            
            if let email = estudante.email {
                Text("Email: \(email)")
            } else {
                Text("Email não informado")
            }
        }
        .padding()
    }
}
```

Resultado:

```txt
Nome: João
Email não informado
```

---

## 16. If let com lista de structs

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
                
                if let email = estudante.email {
                    Text(email)
                        .font(.subheadline)
                } else {
                    Text("Email não informado")
                        .font(.subheadline)
                }
            }
        }
    }
}
```

Nesse exemplo:

- cada estudante pode ter ou não email;
- `if let` verifica se o email existe antes de exibir.

---

## 17. If let com item selecionado

No SwiftUI, é comum usar optional para representar algo selecionado.

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
- ao clicar em um botão, recebe um estudante;
- `if let` exibe o estudante selecionado.

---

## 18. If let com imagem por URL

`URL(string:)` retorna um optional, porque o endereço pode ser inválido.

```swift
let endereco = "https://picsum.photos/200"
let url = URL(string: endereco)
```

O tipo de `url` é:

```swift
URL?
```

Por isso, antes de usar a URL, podemos aplicar `if let`.

```swift
if let url = URL(string: endereco) {
    print(url)
} else {
    print("URL inválida")
}
```

---

## 19. If let com AsyncImage

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
- `URL(string:)` também pode retornar `nil`;
- `if let` garante que a imagem só será carregada se existir uma URL válida.

---

## 20. If let dentro de função

Também podemos usar `if let` dentro de funções.

```swift
func exibirEmail(_ email: String?) -> String {
    if let email {
        return "Email: \(email)"
    } else {
        return "Email não informado"
    }
}
```

Usando:

```swift
print(exibirEmail("teste@email.com"))
print(exibirEmail(nil))
```

Resultado:

```txt
Email: teste@email.com
Email não informado
```

---

## 21. If let x Guard let

`if let` e `guard let` servem para desembrulhar optionals, mas são usados em situações diferentes.

| Estrutura | Melhor uso |
|---|---|
| `if let` | Quando queremos tratar o caso com valor e o caso sem valor no mesmo bloco |
| `guard let` | Quando queremos validar no começo e sair da função se não tiver valor |

Exemplo com `if let`:

```swift
func exibirNome(_ nome: String?) {
    if let nome {
        print("Nome: \(nome)")
    } else {
        print("Nome não informado")
    }
}
```

Exemplo com `guard let`:

```swift
func confirmarNome(_ nome: String?) {
    guard let nome else {
        print("Nome não informado")
        return
    }
    
    print("Nome confirmado: \(nome)")
}
```

---

## 22. If let x Nil Coalescing

Às vezes, em vez de usar `if let`, podemos usar `??`.

Com `if let`:

```swift
let nome: String? = nil

if let nome {
    print(nome)
} else {
    print("Visitante")
}
```

Com `??`:

```swift
let nome: String? = nil

print(nome ?? "Visitante")
```

Os dois exemplos exibem:

```txt
Visitante
```

Use `??` quando quiser apenas um valor padrão simples.

Use `if let` quando precisar executar uma lógica maior.

---

## 23. Exemplo completo

```swift
import SwiftUI

struct Produto: Identifiable {
    let id = UUID()
    let nome: String
    let precoTexto: String
    let imagemURL: String?
}

struct ContentView: View {
    @State private var produtos = [
        Produto(nome: "Teclado", precoTexto: "150.00", imagemURL: "https://picsum.photos/200"),
        Produto(nome: "Mouse", precoTexto: "Swift", imagemURL: nil),
        Produto(nome: "Monitor", precoTexto: "900.00", imagemURL: "https://picsum.photos/201")
    ]
    
    @State private var produtoSelecionado: Produto? = nil
    
    func converterPreco(_ precoTexto: String) -> Double? {
        return Double(precoTexto)
    }
    
    var body: some View {
        NavigationStack {
            VStack(spacing: 16) {
                List(produtos) { produto in
                    Button {
                        produtoSelecionado = produto
                    } label: {
                        VStack(alignment: .leading, spacing: 8) {
                            Text(produto.nome)
                                .font(.headline)
                            
                            if let preco = converterPreco(produto.precoTexto) {
                                Text("Preço: R$ \(String(format: "%.2f", preco))")
                            } else {
                                Text("Preço inválido")
                            }
                            
                            if let imagemURL = produto.imagemURL,
                               let url = URL(string: imagemURL) {
                                AsyncImage(url: url) { image in
                                    image
                                        .resizable()
                                        .scaledToFit()
                                } placeholder: {
                                    ProgressView()
                                }
                                .frame(height: 120)
                            } else {
                                Text("Imagem não disponível")
                            }
                        }
                    }
                }
                
                if let produtoSelecionado {
                    Text("Selecionado: \(produtoSelecionado.nome)")
                        .font(.headline)
                } else {
                    Text("Nenhum produto selecionado")
                }
            }
            .navigationTitle("If Let")
        }
    }
}
```

Nesse exemplo:

- `imagemURL` é opcional;
- `produtoSelecionado` é opcional;
- `converterPreco` retorna `Double?`;
- `if let` trata o preço convertido;
- `if let` trata a URL da imagem;
- `if let` trata o produto selecionado.

---

## 24. Resumo do if let

| Conceito | Exemplo | Significado |
|---|---|---|
| Optional | `String?` | Valor pode existir ou ser `nil` |
| If let | `if let nome { ... }` | Verifica e desembrulha o valor |
| Else | `else { ... }` | Executa quando o valor é `nil` |
| Múltiplos optionals | `if let nome, let email { ... }` | Todos precisam ter valor |
| Conversão | `if let idade = Int(texto)` | Usa o valor apenas se a conversão funcionar |
| SwiftUI | `if let item { Text(item.nome) }` | Exibe dados opcionais com segurança |

---

## Pontos-chave

- `if let` é usado para desembrulhar optionals com segurança.
- O bloco do `if let` só executa se o optional tiver valor.
- O `else` trata o caso em que o optional é `nil`.
- Podemos usar `if let` com um ou mais optionals.
- Podemos combinar `if let` com conversões, como `Int(texto)`.
- Em SwiftUI, `if let` é muito útil para exibir dados opcionais.
- `if let` evita o uso inseguro de `!`.
- Use `??` quando precisar apenas de um valor padrão simples.
- Use `guard let` quando quiser validar no início de uma função e sair se não houver valor.

---

## Desafio

Crie uma tela em SwiftUI com:

- uma struct chamada `Aluno`;
- os campos `nome`, `email` e `idadeTexto`;
- `email` deve ser opcional;
- uma função que converta `idadeTexto` para `Int?`;
- uma lista de alunos;
- exibição de `"Email não informado"` quando o email for `nil`;
- exibição de `"Idade inválida"` quando a conversão falhar;
- um estado opcional para guardar o aluno selecionado;
- um texto exibindo o aluno selecionado com `if let`.

Exemplo esperado:

```txt
Aluno: Marina
Email: marina@email.com
Idade: 21

Aluno: João
Email não informado
Idade inválida

Selecionado: Marina
```