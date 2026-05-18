# Funções em SwiftUI

Em programação, **funções** são blocos de código criados para executar uma tarefa específica.

Elas ajudam a organizar o código, evitar repetição e deixar o programa mais fácil de entender.

No SwiftUI, funções são muito usadas para validar dados, calcular valores, alterar estados, gerar mensagens e separar responsabilidades dentro de uma tela.

---

## 1. O que são funções?

Uma função é um bloco de código que pode ser chamado sempre que precisarmos executar uma ação.

Exemplo sem função:

```swift
print("Olá, Marina!")
print("Olá, João!")
print("Olá, Bianca!")
```

Exemplo com função:

```swift
func cumprimentar(nome: String) {
    print("Olá, \(nome)!")
}

cumprimentar(nome: "Marina")
cumprimentar(nome: "João")
cumprimentar(nome: "Bianca")
```

Resultado:

```txt
Olá, Marina!
Olá, João!
Olá, Bianca!
```

---

## 2. Criando uma função

Para criar uma função em Swift, usamos a palavra-chave `func`.

### Sintaxe

```swift
func nomeDaFuncao() {
    // Código da função
}
```

### Exemplo

```swift
func mostrarMensagem() {
    print("Bem-vindo ao Swift!")
}

mostrarMensagem()
```

Resultado:

```txt
Bem-vindo ao Swift!
```

Nesse exemplo:

- `func` cria a função;
- `mostrarMensagem` é o nome da função;
- o código dentro das chaves `{ }` é executado quando a função é chamada.

---

## 3. Função sem parâmetro e sem retorno

Uma função pode simplesmente executar uma ação, sem receber valores e sem retornar nada.

```swift
func exibirAviso() {
    print("Preencha todos os campos.")
}

exibirAviso()
```

Resultado:

```txt
Preencha todos os campos.
```

---

## 4. Função com parâmetro

Parâmetros são valores que a função recebe para trabalhar.

```swift
func cumprimentar(nome: String) {
    print("Olá, \(nome)!")
}

cumprimentar(nome: "Carlos")
```

Resultado:

```txt
Olá, Carlos!
```

Nesse exemplo:

- `nome` é o parâmetro;
- `String` é o tipo do parâmetro;
- `"Carlos"` é o valor enviado para a função.

---

## 5. Função com mais de um parâmetro

Uma função pode receber vários parâmetros.

```swift
func mostrarEstudante(nome: String, curso: String) {
    print("Nome: \(nome)")
    print("Curso: \(curso)")
}

mostrarEstudante(nome: "Amanda", curso: "Design")
```

Resultado:

```txt
Nome: Amanda
Curso: Design
```

---

## 6. Função com retorno

Uma função pode retornar um valor.

Para isso, usamos `->` seguido do tipo de retorno.

### Sintaxe

```swift
func nomeDaFuncao() -> Tipo {
    return valor
}
```

### Exemplo

```swift
func gerarMensagem() -> String {
    return "Olá, SwiftUI!"
}

let mensagem = gerarMensagem()

print(mensagem)
```

Resultado:

```txt
Olá, SwiftUI!
```

---

## 7. Função com parâmetro e retorno

```swift
func criarSaudacao(nome: String) -> String {
    return "Olá, \(nome)!"
}

let mensagem = criarSaudacao(nome: "Marina")

print(mensagem)
```

Resultado:

```txt
Olá, Marina!
```

Nesse exemplo:

- a função recebe um `nome`;
- cria uma mensagem;
- retorna uma `String`.

---

## 8. Função com cálculo

Funções também podem ser usadas para cálculos.

```swift
func somar(numero1: Int, numero2: Int) -> Int {
    return numero1 + numero2
}

let resultado = somar(numero1: 10, numero2: 5)

print(resultado)
```

Resultado:

```txt
15
```

---

## 9. Função calculando média

```swift
func calcularMedia(nota1: Double, nota2: Double) -> Double {
    return (nota1 + nota2) / 2
}

let media = calcularMedia(nota1: 8.0, nota2: 9.0)

print(media)
```

Resultado:

```txt
8.5
```

---

## 10. Função com condicional

Podemos usar `if`, `else` e outras estruturas dentro de uma função.

```swift
func verificarAprovacao(nota: Double) -> String {
    if nota >= 7 {
        return "Aprovado"
    } else {
        return "Reprovado"
    }
}

let resultado = verificarAprovacao(nota: 8.5)

print(resultado)
```

Resultado:

```txt
Aprovado
```

---

## 11. Função com Bool

```swift
func verificarMaioridade(idade: Int) -> Bool {
    return idade >= 18
}

let maiorDeIdade = verificarMaioridade(idade: 20)

print(maiorDeIdade)
```

Resultado:

```txt
true
```

---

## 12. Função com Array

Funções podem receber arrays como parâmetro.

```swift
func contarEstudantes(nomes: [String]) -> Int {
    return nomes.count
}

let estudantes = ["Marina", "João", "Bianca"]

let quantidade = contarEstudantes(nomes: estudantes)

print(quantidade)
```

Resultado:

```txt
3
```

---

## 13. Função percorrendo Array

```swift
func listarNomes(nomes: [String]) {
    for nome in nomes {
        print(nome)
    }
}

let nomes = ["Amanda", "Carlos", "Lucas"]

listarNomes(nomes: nomes)
```

Resultado:

```txt
Amanda
Carlos
Lucas
```

---

## 14. Função com Optional

Como um valor opcional pode estar vazio, a função pode tratar esse caso.

```swift
func exibirNome(nome: String?) -> String {
    return nome ?? "Nome não informado"
}

print(exibirNome(nome: nil))
print(exibirNome(nome: "Bianca"))
```

Resultado:

```txt
Nome não informado
Bianca
```

---

## 15. Função com guard

O `guard` é muito usado em funções para validar dados antes de continuar.

```swift
func validarNome(_ nome: String) -> String {
    guard !nome.isEmpty else {
        return "Nome inválido"
    }
    
    return "Nome válido: \(nome)"
}

print(validarNome(""))
print(validarNome("João"))
```

Resultado:

```txt
Nome inválido
Nome válido: João
```

Nesse exemplo:

- se `nome` estiver vazio, a função retorna `"Nome inválido"`;
- caso contrário, retorna `"Nome válido"`.

---

## 16. Nome externo e nome interno de parâmetro

Em Swift, os parâmetros podem ter um nome externo e um nome interno.

```swift
func cumprimentar(usuario nome: String) {
    print("Olá, \(nome)!")
}

cumprimentar(usuario: "Marina")
```

Resultado:

```txt
Olá, Marina!
```

Nesse exemplo:

- `usuario` é o nome usado ao chamar a função;
- `nome` é o nome usado dentro da função.

---

## 17. Omitindo o nome externo

Podemos usar `_` para não precisar escrever o nome do parâmetro na chamada.

```swift
func dobrar(_ numero: Int) -> Int {
    return numero * 2
}

let resultado = dobrar(5)

print(resultado)
```

Resultado:

```txt
10
```

Sem o `_`, seria necessário chamar assim:

```swift
dobrar(numero: 5)
```

---

## 18. Funções em SwiftUI

No SwiftUI, podemos criar funções dentro da `struct` da tela.

```swift
import SwiftUI

struct ContentView: View {
    func gerarMensagem() -> String {
        return "Olá, SwiftUI!"
    }
    
    var body: some View {
        Text(gerarMensagem())
    }
}
```

Nesse exemplo:

- `gerarMensagem()` pertence à `ContentView`;
- o `Text` exibe o valor retornado pela função.

---

## 19. Função com Button

Funções são muito úteis para organizar ações de botões.

```swift
import SwiftUI

struct ContentView: View {
    @State private var contador = 0
    
    func aumentarContador() {
        contador += 1
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Text("Contador: \(contador)")
            
            Button("Aumentar") {
                aumentarContador()
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- `contador` começa em `0`;
- o botão chama a função `aumentarContador()`;
- a função altera o valor de `contador`;
- a tela atualiza automaticamente por causa do `@State`.

---

## 20. Função para validar formulário

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    @State private var mensagem = ""
    
    func validarFormulario() {
        if nome.isEmpty {
            mensagem = "Digite seu nome"
        } else {
            mensagem = "Cadastro confirmado para \(nome)"
        }
    }
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Button("Confirmar") {
                validarFormulario()
            }
            
            Text(mensagem)
        }
        .padding()
    }
}
```

Nesse exemplo:

- a função `validarFormulario()` verifica se o campo está vazio;
- se estiver vazio, exibe uma mensagem de aviso;
- se estiver preenchido, confirma o cadastro.

---

## 21. Função retornando texto para SwiftUI

Também podemos criar funções que retornam textos para exibir na tela.

```swift
import SwiftUI

struct ContentView: View {
    @State private var idade = 18
    
    func verificarIdade() -> String {
        if idade >= 18 {
            return "Maior de idade"
        } else {
            return "Menor de idade"
        }
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Stepper("Idade: \(idade)", value: $idade, in: 0...100)
            
            Text(verificarIdade())
        }
        .padding()
    }
}
```

Nesse exemplo, a função retorna uma mensagem de acordo com a idade.

---

## 22. Função retornando cor

Funções também podem retornar outros tipos, como `Color`.

```swift
import SwiftUI

struct ContentView: View {
    @State private var aprovado = false
    
    func corDoStatus() -> Color {
        if aprovado {
            return .green
        } else {
            return .red
        }
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Text(aprovado ? "Aprovado" : "Reprovado")
                .foregroundStyle(corDoStatus())
            
            Button("Alterar status") {
                aprovado.toggle()
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- a função `corDoStatus()` retorna uma cor;
- se `aprovado` for `true`, retorna verde;
- se for `false`, retorna vermelho.

---

## 23. Função com computed property

Às vezes, uma computed property pode ser melhor do que uma função quando o valor é apenas calculado.

Exemplo com função:

```swift
func maiorDeIdade() -> Bool {
    return idade >= 18
}
```

Exemplo com computed property:

```swift
var maiorDeIdade: Bool {
    idade >= 18
}
```

Em SwiftUI, usamos muito computed properties para valores derivados do estado.

```swift
import SwiftUI

struct ContentView: View {
    @State private var idade = 18
    
    var maiorDeIdade: Bool {
        idade >= 18
    }
    
    var body: some View {
        Text(maiorDeIdade ? "Maior de idade" : "Menor de idade")
    }
}
```

---

## 24. Função com struct

Funções podem receber uma `struct` como parâmetro.

```swift
struct Estudante {
    let nome: String
    let curso: String
}

func gerarDescricao(estudante: Estudante) -> String {
    return "\(estudante.nome) está no curso de \(estudante.curso)."
}

let estudante = Estudante(nome: "Carlos", curso: "Programação")

print(gerarDescricao(estudante: estudante))
```

Resultado:

```txt
Carlos está no curso de Programação.
```

---

## 25. Função com struct em SwiftUI

```swift
import SwiftUI

struct Estudante {
    let nome: String
    let curso: String
}

struct ContentView: View {
    let estudante = Estudante(nome: "Carlos", curso: "Programação")
    
    func gerarDescricao(estudante: Estudante) -> String {
        return "\(estudante.nome) está no curso de \(estudante.curso)."
    }
    
    var body: some View {
        Text(gerarDescricao(estudante: estudante))
    }
}
```

Resultado:

```txt
Carlos está no curso de Programação.
```

---

## 26. Função com lista de structs

```swift
struct Estudante {
    let nome: String
    let nota: Double
}

func filtrarAprovados(estudantes: [Estudante]) -> [Estudante] {
    return estudantes.filter { estudante in
        estudante.nota >= 7
    }
}
```

Usando a função:

```swift
let estudantes = [
    Estudante(nome: "Marina", nota: 8.5),
    Estudante(nome: "João", nota: 6.0),
    Estudante(nome: "Bianca", nota: 9.0)
]

let aprovados = filtrarAprovados(estudantes: estudantes)

for estudante in aprovados {
    print(estudante.nome)
}
```

Resultado:

```txt
Marina
Bianca
```

---

## 27. Função com lista de structs em SwiftUI

```swift
import SwiftUI

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
    let nota: Double
}

struct ContentView: View {
    let estudantes = [
        Estudante(nome: "Marina", nota: 8.5),
        Estudante(nome: "João", nota: 6.0),
        Estudante(nome: "Bianca", nota: 9.0)
    ]
    
    func filtrarAprovados() -> [Estudante] {
        return estudantes.filter { estudante in
            estudante.nota >= 7
        }
    }
    
    var body: some View {
        List(filtrarAprovados()) { estudante in
            Text("\(estudante.nome) - Nota: \(String(format: "%.1f", estudante.nota))")
        }
    }
}
```

Nesse exemplo:

- a função `filtrarAprovados()` retorna apenas estudantes com nota maior ou igual a `7`;
- a `List` exibe o resultado.

---

## 28. Separando lógica da interface

Uma boa prática no SwiftUI é evitar colocar muita lógica diretamente dentro do `body`.

Menos recomendado:

```swift
Button("Confirmar") {
    if nome.isEmpty {
        mensagem = "Digite seu nome"
    } else if idade < 18 {
        mensagem = "Cadastro bloqueado"
    } else {
        mensagem = "Cadastro confirmado"
    }
}
```

Mais organizado:

```swift
func confirmarCadastro() {
    if nome.isEmpty {
        mensagem = "Digite seu nome"
    } else if idade < 18 {
        mensagem = "Cadastro bloqueado"
    } else {
        mensagem = "Cadastro confirmado"
    }
}
```

Uso no botão:

```swift
Button("Confirmar") {
    confirmarCadastro()
}
```

Assim o `body` fica mais limpo e fácil de ler.

---

## 29. Exemplo completo

```swift
import SwiftUI

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
    let curso: String
    let nota: Double
}

struct ContentView: View {
    @State private var nome = ""
    @State private var idade = 18
    @State private var mensagem = ""
    
    let estudantes = [
        Estudante(nome: "Marina", curso: "Design", nota: 8.5),
        Estudante(nome: "João", curso: "Programação", nota: 6.0),
        Estudante(nome: "Bianca", curso: "Inovação", nota: 9.0)
    ]
    
    var maiorDeIdade: Bool {
        idade >= 18
    }
    
    func confirmarCadastro() {
        let nomeTratado = nome.trimmingCharacters(in: .whitespaces)
        
        guard !nomeTratado.isEmpty else {
            mensagem = "Digite um nome válido"
            return
        }
        
        if maiorDeIdade {
            mensagem = "Cadastro confirmado para \(nomeTratado)"
        } else {
            mensagem = "Cadastro bloqueado para \(nomeTratado)"
        }
    }
    
    func gerarStatus(nota: Double) -> String {
        if nota >= 7 {
            return "Aprovado"
        } else {
            return "Reprovado"
        }
    }
    
    func estudantesAprovados() -> [Estudante] {
        return estudantes.filter { estudante in
            estudante.nota >= 7
        }
    }
    
    var body: some View {
        NavigationStack {
            List {
                Section("Cadastro") {
                    TextField("Digite seu nome", text: $nome)
                    
                    Stepper("Idade: \(idade)", value: $idade, in: 0...100)
                    
                    Button("Confirmar") {
                        confirmarCadastro()
                    }
                    
                    Text(mensagem)
                }
                
                Section("Estudantes") {
                    ForEach(estudantes) { estudante in
                        VStack(alignment: .leading) {
                            Text(estudante.nome)
                                .font(.headline)
                            
                            Text("Curso: \(estudante.curso)")
                            Text("Nota: \(String(format: "%.1f", estudante.nota))")
                            Text("Status: \(gerarStatus(nota: estudante.nota))")
                        }
                    }
                }
                
                Section("Aprovados") {
                    ForEach(estudantesAprovados()) { estudante in
                        Text(estudante.nome)
                    }
                }
            }
            .navigationTitle("Funções")
        }
    }
}
```

Nesse exemplo:

- `confirmarCadastro()` valida o formulário;
- `gerarStatus(nota:)` retorna se o estudante foi aprovado ou reprovado;
- `estudantesAprovados()` filtra a lista de estudantes;
- o `body` fica mais organizado chamando as funções prontas.

---

## 30. Resumo das funções

| Tipo de função | Exemplo |
|---|---|
| Sem parâmetro e sem retorno | `func mostrarMensagem()` |
| Com parâmetro | `func cumprimentar(nome: String)` |
| Com retorno | `func gerarMensagem() -> String` |
| Com parâmetro e retorno | `func somar(a: Int, b: Int) -> Int` |
| Com Optional | `func exibirNome(nome: String?) -> String` |
| Com Array | `func contarItens(lista: [String]) -> Int` |
| Com Struct | `func gerarDescricao(estudante: Estudante) -> String` |

---

## Pontos-chave

- Funções são blocos de código reutilizáveis.
- Em Swift, usamos `func` para criar funções.
- Funções podem receber parâmetros.
- Funções podem retornar valores.
- O tipo de retorno é indicado com `->`.
- O `return` devolve um valor da função.
- Funções ajudam a evitar repetição de código.
- Funções deixam o `body` do SwiftUI mais limpo.
- Em SwiftUI, funções são muito usadas em botões, validações, filtros e cálculos.
- Funções podem trabalhar com `String`, `Int`, `Double`, `Bool`, `Array`, `Optional` e `Struct`.

---

## Desafio

Crie uma tela em SwiftUI com:

- um `TextField` para digitar o nome;
- um `Stepper` para escolher a idade;
- uma função `validarNome`;
- uma função `verificarMaioridade`;
- uma função `confirmarCadastro`;
- um botão para confirmar;
- um texto exibindo a mensagem final.

Exemplo esperado:

```txt
Nome: Amanda
Idade: 20
Cadastro confirmado para Amanda
```