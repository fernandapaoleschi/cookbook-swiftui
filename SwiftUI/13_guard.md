# Guard em SwiftUI

Em Swift, `guard` é uma estrutura condicional usada para validar uma condição antes de continuar a execução do código.

Ele é muito usado para deixar funções mais organizadas, principalmente quando precisamos verificar se um valor existe, se um campo está preenchido ou se uma regra foi atendida.

No SwiftUI, `guard` aparece bastante em funções de validação, formulários, login, cadastro, conversão de dados e tratamento de optionals.

---

## 1. O que é guard?

O `guard` verifica uma condição obrigatória.

Se a condição for verdadeira, o código continua.

Se a condição for falsa, o bloco `else` é executado e a função precisa ser encerrada com `return`, `throw`, `break` ou `continue`.

### Sintaxe

```swift
guard condição else {
    // Código executado se a condição for falsa
    return
}
```

Exemplo:

```swift
func verificarIdade(idade: Int) {
    guard idade >= 18 else {
        print("Acesso negado")
        return
    }
    
    print("Acesso permitido")
}

verificarIdade(idade: 20)
```

Resultado:

```txt
Acesso permitido
```

---

## 2. Guard com condição falsa

```swift
func verificarIdade(idade: Int) {
    guard idade >= 18 else {
        print("Acesso negado")
        return
    }
    
    print("Acesso permitido")
}

verificarIdade(idade: 16)
```

Resultado:

```txt
Acesso negado
```

Nesse exemplo:

- `idade >= 18` é falso;
- o código entra no `else`;
- a função é encerrada com `return`;
- o restante da função não é executado.

---

## 3. Diferença entre if e guard

O `if` é usado quando queremos executar um bloco se uma condição for verdadeira.

O `guard` é usado quando queremos impedir que o código continue caso uma condição não seja atendida.

Exemplo com `if`:

```swift
func confirmarCadastro(nome: String) {
    if nome.isEmpty {
        print("Digite um nome")
    } else {
        print("Cadastro confirmado para \(nome)")
    }
}
```

Exemplo com `guard`:

```swift
func confirmarCadastro(nome: String) {
    guard !nome.isEmpty else {
        print("Digite um nome")
        return
    }
    
    print("Cadastro confirmado para \(nome)")
}
```

Os dois funcionam, mas o `guard` deixa o fluxo principal mais direto.

---

## 4. Guard com String vazia

O `guard` é muito usado para validar campos de texto.

```swift
func validarNome(_ nome: String) {
    guard !nome.isEmpty else {
        print("Nome inválido")
        return
    }
    
    print("Nome válido: \(nome)")
}

validarNome("")
validarNome("Marina")
```

Resultado:

```txt
Nome inválido
Nome válido: Marina
```

---

## 5. Guard com trimmingCharacters

Às vezes, o usuário digita apenas espaços.

Para tratar isso, usamos `trimmingCharacters(in:)`.

```swift
func validarNome(_ nome: String) {
    let nomeTratado = nome.trimmingCharacters(in: .whitespaces)
    
    guard !nomeTratado.isEmpty else {
        print("Nome inválido")
        return
    }
    
    print("Nome válido: \(nomeTratado)")
}

validarNome("   ")
validarNome("  João  ")
```

Resultado:

```txt
Nome inválido
Nome válido: João
```

Nesse exemplo:

- `"   "` vira uma string vazia;
- `"  João  "` vira `"João"`.

---

## 6. Guard com Optional

O `guard let` é usado para desembrulhar optionals com segurança.

```swift
func exibirNome(_ nome: String?) {
    guard let nome else {
        print("Nome não informado")
        return
    }
    
    print("Nome: \(nome)")
}

exibirNome(nil)
exibirNome("Bianca")
```

Resultado:

```txt
Nome não informado
Nome: Bianca
```

Nesse exemplo:

- se `nome` for `nil`, a função para;
- se `nome` tiver valor, o valor fica disponível depois do `guard`.

---

## 7. Guard let tradicional

Também podemos escrever `guard let` usando outro nome para a variável desembrulhada.

```swift
func exibirEmail(_ email: String?) {
    guard let emailDesembrulhado = email else {
        print("Email não informado")
        return
    }
    
    print("Email: \(emailDesembrulhado)")
}

exibirEmail("teste@email.com")
```

Resultado:

```txt
Email: teste@email.com
```

---

## 8. Guard let simplificado

Em versões mais recentes do Swift, podemos usar o mesmo nome da variável.

```swift
func exibirEmail(_ email: String?) {
    guard let email else {
        print("Email não informado")
        return
    }
    
    print("Email: \(email)")
}
```

Essa forma é mais curta e muito comum em Swift moderno.

---

## 9. Guard com múltiplos optionals

Podemos validar mais de um optional no mesmo `guard`.

```swift
func exibirDados(nome: String?, email: String?) {
    guard let nome, let email else {
        print("Dados incompletos")
        return
    }
    
    print("Nome: \(nome)")
    print("Email: \(email)")
}

exibirDados(nome: "Carlos", email: "carlos@email.com")
exibirDados(nome: "Amanda", email: nil)
```

Resultado:

```txt
Nome: Carlos
Email: carlos@email.com
Dados incompletos
```

Nesse exemplo, o código só continua se `nome` e `email` tiverem valor.

---

## 10. Guard com conversão de tipos

Quando convertemos uma `String` para `Int`, o resultado é um optional.

Por isso, podemos usar `guard let`.

```swift
func validarIdade(_ idadeTexto: String) {
    guard let idade = Int(idadeTexto) else {
        print("Idade inválida")
        return
    }
    
    print("Idade: \(idade)")
}

validarIdade("20")
validarIdade("Swift")
```

Resultado:

```txt
Idade: 20
Idade inválida
```

---

## 11. Guard com condição extra

Podemos combinar `guard let` com outras condições.

```swift
func verificarMaioridade(_ idadeTexto: String) {
    guard let idade = Int(idadeTexto), idade >= 18 else {
        print("Idade inválida ou menor de idade")
        return
    }
    
    print("Maior de idade")
}

verificarMaioridade("20")
verificarMaioridade("16")
verificarMaioridade("Swift")
```

Resultado:

```txt
Maior de idade
Idade inválida ou menor de idade
Idade inválida ou menor de idade
```

---

## 12. Guard em SwiftUI

No SwiftUI, geralmente usamos `guard` dentro de funções chamadas por botões.

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    @State private var mensagem = ""
    
    func confirmarCadastro() {
        guard !nome.isEmpty else {
            mensagem = "Digite seu nome"
            return
        }
        
        mensagem = "Cadastro confirmado para \(nome)"
    }
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Button("Confirmar") {
                confirmarCadastro()
            }
            
            Text(mensagem)
        }
        .padding()
    }
}
```

Nesse exemplo:

- o usuário digita um nome;
- o botão chama `confirmarCadastro()`;
- `guard` verifica se o campo está preenchido;
- se estiver vazio, mostra uma mensagem;
- se estiver preenchido, confirma o cadastro.

---

## 13. Guard com nome tratado em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    @State private var mensagem = ""
    
    func confirmarCadastro() {
        let nomeTratado = nome.trimmingCharacters(in: .whitespaces)
        
        guard !nomeTratado.isEmpty else {
            mensagem = "Digite um nome válido"
            return
        }
        
        mensagem = "Cadastro confirmado para \(nomeTratado)"
    }
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Button("Confirmar") {
                confirmarCadastro()
            }
            
            Text(mensagem)
        }
        .padding()
    }
}
```

Nesse exemplo, se o usuário digitar apenas espaços, o cadastro não será confirmado.

---

## 14. Guard com idade em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    @State private var idadeTexto = ""
    @State private var mensagem = ""
    
    func confirmarIdade() {
        guard let idade = Int(idadeTexto) else {
            mensagem = "Digite uma idade válida"
            return
        }
        
        guard idade >= 18 else {
            mensagem = "Cadastro permitido apenas para maiores de idade"
            return
        }
        
        mensagem = "Cadastro permitido"
    }
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite sua idade", text: $idadeTexto)
                .textFieldStyle(.roundedBorder)
                .keyboardType(.numberPad)
            
            Button("Confirmar") {
                confirmarIdade()
            }
            
            Text(mensagem)
        }
        .padding()
    }
}
```

Nesse exemplo:

- o primeiro `guard` valida se a idade é um número;
- o segundo `guard` valida se a idade é maior ou igual a `18`;
- se alguma validação falhar, a função para.

---

## 15. Guard com formulário

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    @State private var email = ""
    @State private var idadeTexto = ""
    @State private var mensagem = ""
    
    func confirmarCadastro() {
        let nomeTratado = nome.trimmingCharacters(in: .whitespaces)
        let emailTratado = email.trimmingCharacters(in: .whitespaces)
        
        guard !nomeTratado.isEmpty else {
            mensagem = "Digite seu nome"
            return
        }
        
        guard !emailTratado.isEmpty else {
            mensagem = "Digite seu email"
            return
        }
        
        guard let idade = Int(idadeTexto) else {
            mensagem = "Digite uma idade válida"
            return
        }
        
        guard idade >= 18 else {
            mensagem = "Cadastro permitido apenas para maiores de idade"
            return
        }
        
        mensagem = "Cadastro confirmado para \(nomeTratado)"
    }
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            TextField("Email", text: $email)
                .textFieldStyle(.roundedBorder)
            
            TextField("Idade", text: $idadeTexto)
                .textFieldStyle(.roundedBorder)
                .keyboardType(.numberPad)
            
            Button("Confirmar") {
                confirmarCadastro()
            }
            
            Text(mensagem)
                .multilineTextAlignment(.center)
        }
        .padding()
    }
}
```

Nesse exemplo, cada `guard` valida uma regra diferente.

---

## 16. Guard let com item selecionado

Em SwiftUI, é comum usar optional para guardar um item selecionado.

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
    @State private var mensagem = ""
    
    func confirmarSelecao() {
        guard let estudanteSelecionado else {
            mensagem = "Selecione um estudante"
            return
        }
        
        mensagem = "Selecionado: \(estudanteSelecionado.nome)"
    }
    
    var body: some View {
        VStack(spacing: 16) {
            ForEach(estudantes) { estudante in
                Button(estudante.nome) {
                    estudanteSelecionado = estudante
                }
            }
            
            Button("Confirmar seleção") {
                confirmarSelecao()
            }
            
            Text(mensagem)
        }
        .padding()
    }
}
```

Nesse exemplo:

- `estudanteSelecionado` começa como `nil`;
- se o usuário tentar confirmar sem selecionar, aparece uma mensagem;
- se selecionar alguém, a confirmação funciona.

---

## 17. Guard com URL

`URL(string:)` retorna um optional, porque o endereço pode ser inválido.

```swift
func abrirURL(_ endereco: String) {
    guard let url = URL(string: endereco) else {
        print("URL inválida")
        return
    }
    
    print("URL válida: \(url)")
}

abrirURL("https://developer.apple.com")
```

Resultado:

```txt
URL válida: https://developer.apple.com
```

---

## 18. Guard com AsyncImage

```swift
import SwiftUI

struct ContentView: View {
    let enderecoImagem: String? = "https://picsum.photos/200"
    @State private var mensagem = ""
    
    func validarImagem() {
        guard let enderecoImagem,
              let url = URL(string: enderecoImagem) else {
            mensagem = "Imagem não disponível"
            return
        }
        
        mensagem = "Imagem válida: \(url.absoluteString)"
    }
    
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
            
            Button("Validar imagem") {
                validarImagem()
            }
            
            Text(mensagem)
                .multilineTextAlignment(.center)
        }
        .padding()
    }
}
```

Nesse exemplo:

- `enderecoImagem` é opcional;
- `URL(string:)` também retorna optional;
- `guard` valida se existe uma URL antes de continuar.

---

## 19. Guard x If Let

`guard let` e `if let` servem para desembrulhar optionals, mas têm usos diferentes.

| Estrutura | Uso mais comum |
|---|---|
| `if let` | Quando queremos tratar o caso com valor e sem valor dentro da tela ou bloco |
| `guard let` | Quando queremos validar no começo da função e parar se não tiver valor |

Exemplo com `if let`:

```swift
if let nome {
    Text("Olá, \(nome)")
} else {
    Text("Nome não informado")
}
```

Exemplo com `guard let`:

```swift
func confirmar() {
    guard let nome else {
        mensagem = "Nome não informado"
        return
    }
    
    mensagem = "Confirmado: \(nome)"
}
```

---

## 20. Guard com return antecipado

Um dos principais benefícios do `guard` é o **early return**, ou retorno antecipado.

Isso evita muitos blocos `if else` aninhados.

Menos organizado:

```swift
func confirmar(nome: String, idade: Int) {
    if !nome.isEmpty {
        if idade >= 18 {
            print("Cadastro confirmado")
        } else {
            print("Menor de idade")
        }
    } else {
        print("Nome inválido")
    }
}
```

Mais organizado com `guard`:

```swift
func confirmar(nome: String, idade: Int) {
    guard !nome.isEmpty else {
        print("Nome inválido")
        return
    }
    
    guard idade >= 18 else {
        print("Menor de idade")
        return
    }
    
    print("Cadastro confirmado")
}
```

O fluxo principal fica mais limpo.

---

## 21. Exemplo completo

```swift
import SwiftUI

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
    let email: String?
    let idadeTexto: String
}

struct ContentView: View {
    @State private var estudantes = [
        Estudante(nome: "Marina", email: "marina@email.com", idadeTexto: "21"),
        Estudante(nome: "João", email: nil, idadeTexto: "Swift"),
        Estudante(nome: "Bianca", email: "bianca@email.com", idadeTexto: "17")
    ]
    
    @State private var estudanteSelecionado: Estudante? = nil
    @State private var mensagem = ""
    
    func confirmarEstudante() {
        guard let estudanteSelecionado else {
            mensagem = "Selecione um estudante"
            return
        }
        
        guard let email = estudanteSelecionado.email else {
            mensagem = "O estudante não possui email cadastrado"
            return
        }
        
        guard let idade = Int(estudanteSelecionado.idadeTexto) else {
            mensagem = "Idade inválida"
            return
        }
        
        guard idade >= 18 else {
            mensagem = "Estudante menor de idade"
            return
        }
        
        mensagem = """
        Cadastro confirmado
        Nome: \(estudanteSelecionado.nome)
        Email: \(email)
        Idade: \(idade)
        """
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
                            
                            Text(estudante.email ?? "Email não informado")
                            Text("Idade informada: \(estudante.idadeTexto)")
                        }
                    }
                }
                
                if let estudanteSelecionado {
                    Text("Selecionado: \(estudanteSelecionado.nome)")
                } else {
                    Text("Nenhum estudante selecionado")
                }
                
                Button("Confirmar estudante") {
                    confirmarEstudante()
                }
                
                Text(mensagem)
                    .multilineTextAlignment(.center)
            }
            .navigationTitle("Guard")
        }
    }
}
```

Nesse exemplo:

- `estudanteSelecionado` é opcional;
- `email` é opcional;
- `idadeTexto` precisa ser convertido para `Int`;
- cada `guard` valida uma etapa;
- se uma etapa falhar, a função para;
- se tudo estiver correto, o cadastro é confirmado.

---

## 22. Resumo do guard

| Conceito | Exemplo | Significado |
|---|---|---|
| `guard` | `guard idade >= 18 else { return }` | Valida uma condição obrigatória |
| `guard let` | `guard let nome else { return }` | Desembrulha optional com segurança |
| `else` | `else { return }` | Executa quando a condição falha |
| `return` | `return` | Encerra a função |
| Early return | Retorno antecipado | Evita muitos `if else` aninhados |

---

## Pontos-chave

- `guard` valida condições obrigatórias.
- Se a condição falhar, o bloco `else` é executado.
- Dentro do `else`, é obrigatório encerrar o fluxo com `return`, `throw`, `break` ou `continue`.
- `guard let` desembrulha optionals com segurança.
- Depois do `guard let`, o valor desembrulhado pode ser usado no restante da função.
- `guard` ajuda a evitar muitos `if else` aninhados.
- Em SwiftUI, `guard` é muito usado dentro de funções chamadas por botões.
- Use `guard` para validar formulários, conversões, seleções e dados opcionais.

---

## Desafio

Crie uma tela em SwiftUI com:

- uma struct chamada `Produto`;
- os campos `nome`, `precoTexto` e `estoqueTexto`;
- uma lista de produtos;
- um estado opcional para guardar o produto selecionado;
- uma função `confirmarProduto`;
- dentro da função, use `guard` para validar:
  - se existe produto selecionado;
  - se o preço pode ser convertido para `Double`;
  - se o estoque pode ser convertido para `Int`;
  - se o estoque é maior que zero;
- uma mensagem final exibindo o resultado.

Exemplo esperado:

```txt
Selecionado: Teclado

Produto confirmado
Nome: Teclado
Preço: R$ 150.00
Estoque: 10
```