# Optional Chaining em SwiftUI

Em Swift, **Optional Chaining** é uma forma segura de acessar propriedades, métodos ou valores dentro de um optional.

O operador usado é:

```swift
?.
```

Ele permite tentar acessar algo que pode estar `nil`, sem quebrar o aplicativo.

No SwiftUI, Optional Chaining aparece bastante quando trabalhamos com dados opcionais, structs aninhadas, respostas de API, imagens, usuários, produtos e informações que podem não existir.

---

## 1. O que é Optional Chaining?

Optional Chaining significa encadear acessos em valores opcionais.

Exemplo:

```swift
let nome: String? = "marina"

let nomeMaiusculo = nome?.uppercased()

print(nomeMaiusculo)
```

Resultado:

```txt
Optional("MARINA")
```

Nesse exemplo:

- `nome` é uma `String?`;
- usamos `nome?.uppercased()`;
- se `nome` tiver valor, o método `uppercased()` é executado;
- se `nome` for `nil`, o resultado será `nil`.

---

## 2. Optional Chaining com nil

```swift
let nome: String? = nil

let nomeMaiusculo = nome?.uppercased()

print(nomeMaiusculo)
```

Resultado:

```txt
nil
```

Nesse caso, como `nome` está vazio, o Swift não tenta executar `uppercased()`.

Isso evita erro em tempo de execução.

---

## 3. Por que usar Optional Chaining?

Sem optional chaining, precisaríamos desembrulhar o optional antes de acessar o valor.

Exemplo com `if let`:

```swift
let nome: String? = "João"

if let nome {
    print(nome.uppercased())
}
```

Com optional chaining, fica mais curto:

```swift
let nome: String? = "João"

print(nome?.uppercased())
```

Resultado:

```txt
Optional("JOÃO")
```

---

## 4. Optional Chaining com Nil Coalescing

É muito comum combinar `?.` com `??`.

```swift
let nome: String? = "Bianca"

let nomeFormatado = nome?.uppercased() ?? "NOME NÃO INFORMADO"

print(nomeFormatado)
```

Resultado:

```txt
BIANCA
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

- `nome?.uppercased()` tenta transformar o nome em maiúsculo;
- se o resultado for `nil`, o `??` usa o texto padrão.

---

## 5. Diferença entre `?`, `?.` e `??`

| Símbolo | Nome | Uso |
|---|---|---|
| `?` | Optional | Indica que o valor pode ser `nil` |
| `?.` | Optional Chaining | Acessa algo dentro de um optional com segurança |
| `??` | Nil Coalescing | Define um valor padrão se for `nil` |

Exemplo:

```swift
let nome: String? = nil

let resultado = nome?.uppercased() ?? "Visitante"
```

Nesse exemplo:

- `String?` cria um optional;
- `?.` tenta acessar `uppercased()`;
- `??` define `"Visitante"` se o resultado for `nil`.

---

## 6. Optional Chaining em SwiftUI

No SwiftUI, podemos usar optional chaining dentro de um `Text`.

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = "marina"
    
    var body: some View {
        Text(nome?.uppercased() ?? "NOME NÃO INFORMADO")
    }
}
```

Resultado exibido na tela:

```txt
MARINA
```

---

## 7. Optional Chaining em SwiftUI com nil

```swift
import SwiftUI

struct ContentView: View {
    let nome: String? = nil
    
    var body: some View {
        Text(nome?.uppercased() ?? "NOME NÃO INFORMADO")
    }
}
```

Resultado:

```txt
NOME NÃO INFORMADO
```

---

## 8. Optional Chaining com propriedades

Optional chaining também pode acessar propriedades.

```swift
struct Estudante {
    let nome: String
    let email: String?
}

let estudante: Estudante? = Estudante(nome: "Carlos", email: "carlos@email.com")

print(estudante?.nome)
print(estudante?.email)
```

Resultado:

```txt
Optional("Carlos")
Optional("carlos@email.com")
```

Nesse exemplo:

- `estudante` é opcional;
- usamos `estudante?.nome`;
- se `estudante` existir, acessamos `nome`;
- se `estudante` for `nil`, o resultado será `nil`.

---

## 9. Optional Chaining com propriedade opcional

```swift
struct Estudante {
    let nome: String
    let email: String?
}

let estudante: Estudante? = Estudante(nome: "Amanda", email: nil)

let email = estudante?.email ?? "Email não informado"

print(email)
```

Resultado:

```txt
Email não informado
```

Aqui existem dois pontos importantes:

- `estudante` pode ser `nil`;
- `email` também pode ser `nil`.

O `??` garante um valor padrão no final.

---

## 10. Optional Chaining com structs aninhadas

Em projetos reais, é comum ter uma struct dentro de outra.

```swift
struct Endereco {
    let cidade: String
    let estado: String
}

struct Usuario {
    let nome: String
    let endereco: Endereco?
}
```

Exemplo:

```swift
let usuario: Usuario? = Usuario(
    nome: "Marina",
    endereco: Endereco(cidade: "Recife", estado: "PE")
)

let cidade = usuario?.endereco?.cidade ?? "Cidade não informada"

print(cidade)
```

Resultado:

```txt
Recife
```

Nesse exemplo:

```swift
usuario?.endereco?.cidade
```

significa:

- se `usuario` existir, tente acessar `endereco`;
- se `endereco` existir, tente acessar `cidade`;
- se qualquer parte for `nil`, o resultado final será `nil`.

---

## 11. Struct aninhada com nil

```swift
let usuario: Usuario? = Usuario(
    nome: "João",
    endereco: nil
)

let cidade = usuario?.endereco?.cidade ?? "Cidade não informada"

print(cidade)
```

Resultado:

```txt
Cidade não informada
```

Como `endereco` é `nil`, o Swift não tenta acessar `cidade`.

---

## 12. Optional Chaining em SwiftUI com struct aninhada

```swift
import SwiftUI

struct Endereco {
    let cidade: String
    let estado: String
}

struct Usuario {
    let nome: String
    let endereco: Endereco?
}

struct ContentView: View {
    let usuario: Usuario? = Usuario(
        nome: "Marina",
        endereco: Endereco(cidade: "Recife", estado: "PE")
    )
    
    var body: some View {
        VStack(alignment: .leading, spacing: 8) {
            Text("Nome: \(usuario?.nome ?? "Nome não informado")")
            Text("Cidade: \(usuario?.endereco?.cidade ?? "Cidade não informada")")
            Text("Estado: \(usuario?.endereco?.estado ?? "Estado não informado")")
        }
        .padding()
    }
}
```

Resultado:

```txt
Nome: Marina
Cidade: Recife
Estado: PE
```

---

## 13. Optional Chaining em lista de structs

```swift
import SwiftUI

struct Endereco {
    let cidade: String
    let estado: String
}

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
    let endereco: Endereco?
}

struct ContentView: View {
    let estudantes = [
        Estudante(nome: "Marina", endereco: Endereco(cidade: "Recife", estado: "PE")),
        Estudante(nome: "João", endereco: nil),
        Estudante(nome: "Bianca", endereco: Endereco(cidade: "Olinda", estado: "PE"))
    ]
    
    var body: some View {
        List(estudantes) { estudante in
            VStack(alignment: .leading, spacing: 6) {
                Text(estudante.nome)
                    .font(.headline)
                
                Text("Cidade: \(estudante.endereco?.cidade ?? "Não informada")")
                Text("Estado: \(estudante.endereco?.estado ?? "Não informado")")
            }
        }
    }
}
```

Nesse exemplo:

- alguns estudantes têm endereço;
- outros estão com `endereco` como `nil`;
- `estudante.endereco?.cidade` acessa a cidade apenas se o endereço existir.

---

## 14. Optional Chaining com métodos

Também podemos chamar métodos usando optional chaining.

```swift
let nome: String? = "carlos"

let quantidadeDeLetras = nome?.count

print(quantidadeDeLetras)
```

Resultado:

```txt
Optional(6)
```

Outro exemplo:

```swift
let texto: String? = "swiftui"

let resultado = texto?.capitalized

print(resultado)
```

Resultado:

```txt
Optional("Swiftui")
```

---

## 15. Optional Chaining com arrays

Um array também pode ser opcional.

```swift
let nomes: [String]? = ["Marina", "João", "Bianca"]

let quantidade = nomes?.count ?? 0

print(quantidade)
```

Resultado:

```txt
3
```

Agora com `nil`:

```swift
let nomes: [String]? = nil

let quantidade = nomes?.count ?? 0

print(quantidade)
```

Resultado:

```txt
0
```

---

## 16. Optional Chaining com primeiro item

```swift
let nomes: [String]? = ["Marina", "João", "Bianca"]

let primeiroNome = nomes?.first ?? "Nenhum nome encontrado"

print(primeiroNome)
```

Resultado:

```txt
Marina
```

Agora com array vazio:

```swift
let nomes: [String]? = []

let primeiroNome = nomes?.first ?? "Nenhum nome encontrado"

print(primeiroNome)
```

Resultado:

```txt
Nenhum nome encontrado
```

---

## 17. Optional Chaining com array em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let nomes: [String]? = ["Marina", "João", "Bianca"]
    
    var body: some View {
        VStack(spacing: 8) {
            Text("Quantidade: \(nomes?.count ?? 0)")
            Text("Primeiro nome: \(nomes?.first ?? "Nenhum nome")")
        }
        .padding()
    }
}
```

Resultado:

```txt
Quantidade: 3
Primeiro nome: Marina
```

---

## 18. Optional Chaining com dictionary

```swift
let estudante: [String: String]? = [
    "nome": "Carlos",
    "curso": "Programação"
]

let nome = estudante?["nome"] ?? "Nome não informado"
let curso = estudante?["curso"] ?? "Curso não informado"

print(nome)
print(curso)
```

Resultado:

```txt
Carlos
Programação
```

Nesse exemplo:

- `estudante` é um dicionário opcional;
- `estudante?["nome"]` tenta acessar a chave `"nome"` apenas se o dicionário existir;
- `??` define um valor padrão caso não exista.

---

## 19. Optional Chaining com dictionary em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let estudante: [String: String]? = [
        "nome": "Carlos",
        "curso": "Programação"
    ]
    
    var body: some View {
        VStack(alignment: .leading, spacing: 8) {
            Text("Nome: \(estudante?["nome"] ?? "Não informado")")
            Text("Curso: \(estudante?["curso"] ?? "Não informado")")
            Text("Turno: \(estudante?["turno"] ?? "Não informado")")
        }
        .padding()
    }
}
```

Resultado:

```txt
Nome: Carlos
Curso: Programação
Turno: Não informado
```

---

## 20. Optional Chaining com URL

`URL(string:)` retorna um optional, porque o endereço pode ser inválido.

```swift
let enderecoImagem: String? = "https://picsum.photos/200"

let url = enderecoImagem.flatMap { URL(string: $0) }

print(url)
```

Resultado:

```txt
Optional(https://picsum.photos/200)
```

Também podemos usar `if let` para validar antes de usar.

---

## 21. Optional Chaining com AsyncImage

```swift
import SwiftUI

struct Produto {
    let nome: String
    let imagemURL: String?
}

struct ContentView: View {
    let produto = Produto(
        nome: "Teclado",
        imagemURL: "https://picsum.photos/200"
    )
    
    var urlImagem: URL? {
        produto.imagemURL.flatMap { URL(string: $0) }
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Text(produto.nome)
                .font(.headline)
            
            if let urlImagem {
                AsyncImage(url: urlImagem) { image in
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

- `imagemURL` é opcional;
- `flatMap` tenta transformar a `String` em `URL`;
- se a URL for válida, a imagem aparece;
- se não for, aparece `"Imagem não disponível"`.

---

## 22. Optional Chaining x If Let

O optional chaining é ótimo quando queremos acessar um valor de forma curta.

```swift
let cidade = usuario?.endereco?.cidade ?? "Cidade não informada"
```

O `if let` é melhor quando precisamos executar uma lógica maior.

```swift
if let endereco = usuario?.endereco {
    Text("Cidade: \(endereco.cidade)")
    Text("Estado: \(endereco.estado)")
} else {
    Text("Endereço não informado")
}
```

Use optional chaining para acessos simples.

Use `if let` quando precisar mostrar componentes diferentes ou executar mais regras.

---

## 23. Optional Chaining x Guard Let

O `guard let` é melhor dentro de funções, quando queremos parar a execução se algum valor estiver ausente.

Com optional chaining:

```swift
let cidade = usuario?.endereco?.cidade ?? "Cidade não informada"
```

Com `guard let`:

```swift
func confirmar(usuario: Usuario?) {
    guard let usuario else {
        print("Usuário não informado")
        return
    }
    
    guard let endereco = usuario.endereco else {
        print("Endereço não informado")
        return
    }
    
    print("Cidade: \(endereco.cidade)")
}
```

---

## 24. Cuidado com muitos encadeamentos

Optional chaining pode deixar o código muito curto, mas também pode ficar difícil de ler quando tem muitos níveis.

Exemplo:

```swift
let cidade = usuario?.perfil?.endereco?.cidade?.uppercased() ?? "CIDADE NÃO INFORMADA"
```

Funciona, mas pode ficar confuso.

Nesses casos, pode ser melhor separar em partes:

```swift
let cidade = usuario?.perfil?.endereco?.cidade
let cidadeFormatada = cidade?.uppercased() ?? "CIDADE NÃO INFORMADA"
```

Ou usar `if let`.

---

## 25. Exemplo completo

```swift
import SwiftUI

struct Endereco {
    let cidade: String
    let estado: String
}

struct Perfil {
    let bio: String?
    let endereco: Endereco?
}

struct Usuario: Identifiable {
    let id = UUID()
    let nome: String
    let email: String?
    let perfil: Perfil?
}

struct ContentView: View {
    @State private var usuarios = [
        Usuario(
            nome: "Marina",
            email: "marina@email.com",
            perfil: Perfil(
                bio: "Estudante de Design",
                endereco: Endereco(cidade: "Recife", estado: "PE")
            )
        ),
        Usuario(
            nome: "João",
            email: nil,
            perfil: Perfil(
                bio: nil,
                endereco: nil
            )
        ),
        Usuario(
            nome: "Bianca",
            email: "bianca@email.com",
            perfil: nil
        )
    ]
    
    var body: some View {
        NavigationStack {
            List(usuarios) { usuario in
                VStack(alignment: .leading, spacing: 8) {
                    Text(usuario.nome)
                        .font(.headline)
                    
                    Text("Email: \(usuario.email ?? "Não informado")")
                    
                    Text("Bio: \(usuario.perfil?.bio ?? "Bio não informada")")
                    
                    Text("Cidade: \(usuario.perfil?.endereco?.cidade ?? "Cidade não informada")")
                    
                    Text("Estado: \(usuario.perfil?.endereco?.estado ?? "Estado não informado")")
                }
            }
            .navigationTitle("Optional Chaining")
        }
    }
}
```

Resultado esperado:

```txt
Marina
Email: marina@email.com
Bio: Estudante de Design
Cidade: Recife
Estado: PE

João
Email: Não informado
Bio: Bio não informada
Cidade: Cidade não informada
Estado: Estado não informado

Bianca
Email: bianca@email.com
Bio: Bio não informada
Cidade: Cidade não informada
Estado: Estado não informado
```

---

## 26. Resumo do Optional Chaining

| Conceito | Exemplo | Significado |
|---|---|---|
| Optional | `String?` | Valor pode existir ou ser `nil` |
| Optional Chaining | `nome?.uppercased()` | Acessa método se houver valor |
| Propriedade opcional | `usuario?.nome` | Acessa propriedade se o objeto existir |
| Struct aninhada | `usuario?.endereco?.cidade` | Acessa vários níveis com segurança |
| Com valor padrão | `nome?.uppercased() ?? "Sem nome"` | Usa `??` se o resultado for `nil` |
| Array opcional | `nomes?.count ?? 0` | Conta se o array existir |
| Dictionary opcional | `dados?["nome"] ?? "Sem nome"` | Acessa chave se o dicionário existir |

---

## Pontos-chave

- Optional Chaining usa o operador `?.`.
- Ele permite acessar propriedades e métodos de valores opcionais.
- Se qualquer parte do encadeamento for `nil`, o resultado final será `nil`.
- É comum combinar `?.` com `??`.
- Optional Chaining ajuda a evitar uso inseguro de `!`.
- Em SwiftUI, é útil para dados opcionais, structs aninhadas, listas, APIs e imagens.
- Use `if let` quando precisar de uma lógica maior.
- Use `guard let` quando precisar validar valores dentro de uma função.
- Evite encadeamentos longos demais se eles prejudicarem a leitura.

---

## Desafio

Crie uma tela em SwiftUI com:

- uma struct chamada `Endereco`;
- uma struct chamada `Perfil`;
- uma struct chamada `Aluno`;
- `Aluno` deve ter `nome`, `email` e `perfil`;
- `email` deve ser opcional;
- `perfil` deve ser opcional;
- `Perfil` deve ter `bio` e `endereco`;
- `bio` e `endereco` devem ser opcionais;
- use optional chaining para exibir cidade e estado;
- use nil coalescing para mensagens padrão.

Exemplo esperado:

```txt
Aluno: Marina
Email: marina@email.com
Bio: Estudante de Design
Cidade: Recife
Estado: PE

Aluno: João
Email: Não informado
Bio: Bio não informada
Cidade: Cidade não informada
Estado: Estado não informado
```