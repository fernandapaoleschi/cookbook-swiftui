# Condicionais em SwiftUI

Em programação, **condicionais** são estruturas usadas para executar um bloco de código apenas quando uma condição é verdadeira.

No Swift, usamos condicionais para tomar decisões dentro do código.

No SwiftUI, condicionais são muito usadas para mostrar ou esconder elementos da tela, alterar textos, mudar cores, habilitar botões e controlar estados da interface.

---

## 1. O que são condicionais?

Condicionais permitem que o programa tome decisões.

Exemplo:

```swift
let idade = 18

if idade >= 18 {
    print("Maior de idade")
}
```

Nesse exemplo, a mensagem só será exibida se a idade for maior ou igual a `18`.

Resultado:

```txt
Maior de idade
```

---

## 2. If

O `if` é usado para executar um código quando uma condição é verdadeira.

### Sintaxe

```swift
if condição {
    // Código executado se a condição for verdadeira
}
```

### Exemplo

```swift
let nota = 8

if nota >= 7 {
    print("Aprovado")
}
```

Resultado:

```txt
Aprovado
```

---

## 3. If em SwiftUI

No SwiftUI, podemos usar `if` para decidir o que será exibido na tela.

```swift
import SwiftUI

struct ContentView: View {
    let estaLogado = true
    
    var body: some View {
        VStack {
            if estaLogado {
                Text("Bem-vindo!")
            }
        }
    }
}
```

Nesse exemplo, o texto `"Bem-vindo!"` só aparece se `estaLogado` for `true`.

---

## 4. If Else

O `if else` permite executar um código quando a condição é verdadeira e outro código quando ela é falsa.

### Sintaxe

```swift
if condição {
    // Código se a condição for verdadeira
} else {
    // Código se a condição for falsa
}
```

### Exemplo

```swift
let idade = 16

if idade >= 18 {
    print("Maior de idade")
} else {
    print("Menor de idade")
}
```

Resultado:

```txt
Menor de idade
```

---

## 5. If Else em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let idade = 16
    
    var body: some View {
        VStack {
            if idade >= 18 {
                Text("Maior de idade")
            } else {
                Text("Menor de idade")
            }
        }
    }
}
```

Resultado exibido na tela:

```txt
Menor de idade
```

---

## 6. Else If

O `else if` é usado quando temos mais de uma condição para verificar.

### Sintaxe

```swift
if condição1 {
    // Código se a condição1 for verdadeira
} else if condição2 {
    // Código se a condição2 for verdadeira
} else {
    // Código se nenhuma condição for verdadeira
}
```

### Exemplo

```swift
let nota = 8

if nota >= 9 {
    print("Excelente")
} else if nota >= 7 {
    print("Aprovado")
} else {
    print("Reprovado")
}
```

Resultado:

```txt
Aprovado
```

---

## 7. Else If em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let nota = 8
    
    var body: some View {
        VStack {
            if nota >= 9 {
                Text("Excelente")
            } else if nota >= 7 {
                Text("Aprovado")
            } else {
                Text("Reprovado")
            }
        }
    }
}
```

Resultado:

```txt
Aprovado
```

---

## 8. Condições com Bool

O tipo `Bool` armazena apenas dois valores:

```swift
true
false
```

Exemplo:

```swift
let estaAtivo = true

if estaAtivo {
    print("Status ativo")
} else {
    print("Status inativo")
}
```

Resultado:

```txt
Status ativo
```

---

## 9. Bool em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let estaAtivo = true
    
    var body: some View {
        Text(estaAtivo ? "Ativo" : "Inativo")
    }
}
```

Resultado:

```txt
Ativo
```

Nesse exemplo, usamos o operador ternário, que é uma forma curta de escrever uma condição.

---

## 10. Operadores de comparação

As condicionais geralmente usam operadores de comparação.

| Operador | Significado | Exemplo |
|---|---|---|
| `==` | Igual | `idade == 18` |
| `!=` | Diferente | `nome != "João"` |
| `>` | Maior que | `nota > 7` |
| `<` | Menor que | `idade < 18` |
| `>=` | Maior ou igual | `idade >= 18` |
| `<=` | Menor ou igual | `nota <= 10` |

Exemplo:

```swift
let idade = 20

if idade >= 18 {
    print("Pode continuar")
}
```

Resultado:

```txt
Pode continuar
```

---

## 11. Operadores lógicos

Podemos combinar condições usando operadores lógicos.

| Operador | Nome | Uso |
|---|---|---|
| `&&` | E | Todas as condições precisam ser verdadeiras |
| `||` | OU | Pelo menos uma condição precisa ser verdadeira |
| `!` | NÃO | Inverte uma condição |

---

## 12. Condicional com &&

O operador `&&` retorna verdadeiro apenas quando todas as condições são verdadeiras.

```swift
let idade = 20
let aceitouTermos = true

if idade >= 18 && aceitouTermos {
    print("Cadastro permitido")
} else {
    print("Cadastro bloqueado")
}
```

Resultado:

```txt
Cadastro permitido
```

---

## 13. Condicional com ||

O operador `||` retorna verdadeiro quando pelo menos uma condição é verdadeira.

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

## 14. Condicional com !

O operador `!` inverte o valor lógico.

```swift
let estaBloqueado = false

if !estaBloqueado {
    print("Acesso permitido")
} else {
    print("Acesso bloqueado")
}
```

Resultado:

```txt
Acesso permitido
```

---

## 15. Condicionais com @State

No SwiftUI, é muito comum usar condicionais junto com `@State`.

Isso permite mudar a interface conforme o usuário interage com a tela.

```swift
import SwiftUI

struct ContentView: View {
    @State private var estaLogado = false
    
    var body: some View {
        VStack(spacing: 16) {
            if estaLogado {
                Text("Usuário logado")
            } else {
                Text("Usuário deslogado")
            }
            
            Button("Alterar status") {
                estaLogado.toggle()
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- `estaLogado` começa como `false`;
- a tela mostra `"Usuário deslogado"`;
- ao clicar no botão, o valor muda;
- a interface atualiza automaticamente.

---

## 16. Mostrando e escondendo elementos

Podemos usar `if` para mostrar ou esconder componentes da tela.

```swift
import SwiftUI

struct ContentView: View {
    @State private var mostrarMensagem = false
    
    var body: some View {
        VStack(spacing: 16) {
            Button("Mostrar/Ocultar mensagem") {
                mostrarMensagem.toggle()
            }
            
            if mostrarMensagem {
                Text("Mensagem exibida!")
                    .font(.headline)
            }
        }
        .padding()
    }
}
```

Nesse exemplo, o texto só aparece quando `mostrarMensagem` é `true`.

---

## 17. Alterando texto com condicional

```swift
import SwiftUI

struct ContentView: View {
    @State private var estaOnline = false
    
    var body: some View {
        VStack(spacing: 16) {
            Text(estaOnline ? "Online" : "Offline")
            
            Button("Alterar status") {
                estaOnline.toggle()
            }
        }
        .padding()
    }
}
```

Nesse exemplo, o texto muda entre `"Online"` e `"Offline"`.

---

## 18. Alterando cor com condicional

```swift
import SwiftUI

struct ContentView: View {
    @State private var estaOnline = false
    
    var body: some View {
        VStack(spacing: 16) {
            Text(estaOnline ? "Online" : "Offline")
                .foregroundStyle(estaOnline ? .green : .red)
            
            Button("Alterar status") {
                estaOnline.toggle()
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- se `estaOnline` for `true`, o texto fica verde;
- se for `false`, o texto fica vermelho.

---

## 19. Habilitando e desabilitando botão

Podemos usar condicionais para controlar se um botão pode ou não ser clicado.

```swift
import SwiftUI

struct ContentView: View {
    @State private var aceitouTermos = false
    
    var body: some View {
        VStack(spacing: 16) {
            Toggle("Aceito os termos", isOn: $aceitouTermos)
            
            Button("Continuar") {
                print("Continuando...")
            }
            .disabled(!aceitouTermos)
        }
        .padding()
    }
}
```

Nesse exemplo:

- enquanto `aceitouTermos` for `false`, o botão fica desabilitado;
- quando o usuário ativa o `Toggle`, o botão fica habilitado.

---

## 20. Condicional com TextField

Podemos validar dados digitados pelo usuário.

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            if nome.isEmpty {
                Text("Digite um nome para continuar")
                    .foregroundStyle(.red)
            } else {
                Text("Olá, \(nome)!")
                    .foregroundStyle(.green)
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- se o campo estiver vazio, aparece uma mensagem de aviso;
- se o usuário digitar um nome, aparece uma saudação.

---

## 21. Condicional com idade

```swift
import SwiftUI

struct ContentView: View {
    @State private var idade = 18
    
    var body: some View {
        VStack(spacing: 16) {
            Stepper("Idade: \(idade)", value: $idade, in: 0...100)
            
            if idade >= 18 {
                Text("Maior de idade")
                    .foregroundStyle(.green)
            } else {
                Text("Menor de idade")
                    .foregroundStyle(.red)
            }
        }
        .padding()
    }
}
```

Nesse exemplo, a mensagem muda conforme a idade escolhida.

---

## 22. Condicional com nota

```swift
import SwiftUI

struct ContentView: View {
    @State private var nota = 7.0
    
    var body: some View {
        VStack(spacing: 16) {
            Slider(value: $nota, in: 0...10)
            
            Text("Nota: \(String(format: "%.1f", nota))")
            
            if nota >= 9 {
                Text("Excelente")
                    .foregroundStyle(.green)
            } else if nota >= 7 {
                Text("Aprovado")
                    .foregroundStyle(.blue)
            } else {
                Text("Reprovado")
                    .foregroundStyle(.red)
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- nota maior ou igual a `9` mostra `"Excelente"`;
- nota maior ou igual a `7` mostra `"Aprovado"`;
- nota menor que `7` mostra `"Reprovado"`.

---

## 23. Switch

O `switch` é uma estrutura condicional usada quando temos várias possibilidades para uma mesma variável.

Ele deixa o código mais organizado em casos com muitas opções.

### Sintaxe

```swift
switch valor {
case opcao1:
    // Código
case opcao2:
    // Código
default:
    // Código caso nenhuma opção seja atendida
}
```

### Exemplo

```swift
let curso = "Design"

switch curso {
case "Design":
    print("Curso de Design selecionado")
case "Programação":
    print("Curso de Programação selecionado")
case "Inovação":
    print("Curso de Inovação selecionado")
default:
    print("Curso não encontrado")
}
```

Resultado:

```txt
Curso de Design selecionado
```

---

## 24. Switch em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    @State private var cursoSelecionado = "Design"
    
    let cursos = ["Design", "Programação", "Inovação"]
    
    var mensagemCurso: String {
        switch cursoSelecionado {
        case "Design":
            return "Você escolheu Design"
        case "Programação":
            return "Você escolheu Programação"
        case "Inovação":
            return "Você escolheu Inovação"
        default:
            return "Curso não encontrado"
        }
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Picker("Curso", selection: $cursoSelecionado) {
                ForEach(cursos, id: \.self) { curso in
                    Text(curso)
                }
            }
            .pickerStyle(.menu)
            
            Text(mensagemCurso)
        }
        .padding()
    }
}
```

Nesse exemplo:

- o `Picker` altera o curso selecionado;
- o `switch` retorna uma mensagem diferente para cada curso;
- o texto da tela muda conforme a opção escolhida.

---

## 25. Enum com Switch

Em Swift, `switch` combina muito bem com `enum`.

```swift
enum StatusUsuario {
    case ativo
    case inativo
    case bloqueado
}
```

Exemplo:

```swift
let status = StatusUsuario.ativo

switch status {
case .ativo:
    print("Usuário ativo")
case .inativo:
    print("Usuário inativo")
case .bloqueado:
    print("Usuário bloqueado")
}
```

Resultado:

```txt
Usuário ativo
```

---

## 26. Enum com Switch em SwiftUI

```swift
import SwiftUI

enum StatusUsuario {
    case ativo
    case inativo
    case bloqueado
}

struct ContentView: View {
    @State private var status: StatusUsuario = .ativo
    
    var mensagemStatus: String {
        switch status {
        case .ativo:
            return "Usuário ativo"
        case .inativo:
            return "Usuário inativo"
        case .bloqueado:
            return "Usuário bloqueado"
        }
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Text(mensagemStatus)
            
            Button("Ativar") {
                status = .ativo
            }
            
            Button("Inativar") {
                status = .inativo
            }
            
            Button("Bloquear") {
                status = .bloqueado
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- `status` começa como `.ativo`;
- cada botão altera o valor do `status`;
- o `switch` muda a mensagem exibida na tela.

---

## 27. Guard

O `guard` é uma estrutura condicional usada para validar algo logo no início de uma função.

Se a condição não for atendida, o código sai da função.

### Exemplo

```swift
func validarNome(_ nome: String) {
    guard !nome.isEmpty else {
        print("Nome inválido")
        return
    }
    
    print("Nome válido: \(nome)")
}
```

Chamando a função:

```swift
validarNome("")
validarNome("Marina")
```

Resultado:

```txt
Nome inválido
Nome válido: Marina
```

---

## 28. Guard em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    @State private var mensagem = ""
    
    func confirmarCadastro() {
        guard !nome.isEmpty else {
            mensagem = "Digite um nome antes de continuar"
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

- se `nome` estiver vazio, a função exibe uma mensagem de erro;
- se `nome` tiver valor, o cadastro é confirmado.

---

## 29. Exemplo completo

```swift
import SwiftUI

enum StatusCadastro {
    case pendente
    case aprovado
    case recusado
}

struct ContentView: View {
    @State private var nome = ""
    @State private var idade = 18
    @State private var aceitouTermos = false
    @State private var statusCadastro: StatusCadastro = .pendente
    @State private var mensagem = ""
    
    var maiorDeIdade: Bool {
        idade >= 18
    }
    
    var podeCadastrar: Bool {
        maiorDeIdade && aceitouTermos && !nome.isEmpty
    }
    
    var textoStatus: String {
        switch statusCadastro {
        case .pendente:
            return "Cadastro pendente"
        case .aprovado:
            return "Cadastro aprovado"
        case .recusado:
            return "Cadastro recusado"
        }
    }
    
    func confirmarCadastro() {
        guard !nome.isEmpty else {
            mensagem = "Digite seu nome"
            statusCadastro = .recusado
            return
        }
        
        if podeCadastrar {
            mensagem = "Cadastro realizado com sucesso para \(nome)"
            statusCadastro = .aprovado
        } else {
            mensagem = "Cadastro não permitido"
            statusCadastro = .recusado
        }
    }
    
    var body: some View {
        VStack(spacing: 20) {
            Text("Condicionais em SwiftUI")
                .font(.title2)
                .bold()
            
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Stepper("Idade: \(idade)", value: $idade, in: 0...100)
            
            Toggle("Aceito os termos", isOn: $aceitouTermos)
            
            if maiorDeIdade {
                Text("Maior de idade")
                    .foregroundStyle(.green)
            } else {
                Text("Menor de idade")
                    .foregroundStyle(.red)
            }
            
            Text(textoStatus)
            
            Button("Confirmar cadastro") {
                confirmarCadastro()
            }
            .disabled(!podeCadastrar)
            
            Text(mensagem)
                .multilineTextAlignment(.center)
        }
        .padding()
    }
}
```

Resultado esperado ao preencher corretamente:

```txt
Condicionais em SwiftUI
Maior de idade
Cadastro aprovado
Cadastro realizado com sucesso
```

---

## 30. Resumo das condicionais

| Estrutura | Uso |
|---|---|
| `if` | Executa um código se a condição for verdadeira |
| `else` | Executa um código se a condição do `if` for falsa |
| `else if` | Testa uma nova condição |
| `switch` | Avalia várias possibilidades |
| `guard` | Valida uma condição e encerra a função se falhar |
| Operador ternário | Escreve uma condição curta |

---

## Pontos-chave

- Condicionais permitem que o código tome decisões.
- `if` executa um código se a condição for verdadeira.
- `else` executa um código quando a condição é falsa.
- `else if` permite testar várias condições.
- `switch` é útil quando existem muitas possibilidades.
- `guard` é usado para validar condições antes de continuar uma função.
- Operadores como `==`, `!=`, `>`, `<`, `>=` e `<=` são muito usados em condicionais.
- Operadores lógicos como `&&`, `||` e `!` combinam condições.
- No SwiftUI, condicionais podem mostrar, esconder, alterar ou bloquear componentes da tela.

---

## Desafio

Crie uma tela em SwiftUI com:

- um `TextField` para digitar o nome;
- um `Stepper` para escolher a idade;
- um `Toggle` para aceitar os termos;
- uma mensagem informando se a pessoa é maior ou menor de idade;
- um botão que só fique habilitado quando:
  - o nome não estiver vazio;
  - a idade for maior ou igual a 18;
  - os termos forem aceitos;
- uma mensagem final ao confirmar o cadastro.

Exemplo esperado:

```txt
Nome: João
Idade: 20
Maior de idade
Cadastro permitido
```