# Escopos em SwiftUI

Em programação, **escopo** define onde uma variável, constante, função ou tipo pode ser acessado dentro do código.

Em Swift, o escopo é delimitado principalmente por chaves `{ }`.

No SwiftUI, entender escopos é muito importante, porque usamos estruturas como `struct`, `body`, funções, propriedades, `@State`, `Button`, `if`, `ForEach` e outras partes que possuem seus próprios blocos de código.

---

## 1. O que é escopo?

Escopo é a área do código onde uma informação existe e pode ser usada.

Exemplo:

```swift
let nome = "Marina"

print(nome)
```

Nesse caso, a constante `nome` pode ser usada depois da sua criação.

Resultado:

```txt
Marina
```

---

## 2. Escopo global

O escopo global é a área fora de funções, structs, classes ou blocos.

Tudo que é criado no escopo global pode ser acessado por diferentes partes do arquivo.

```swift
let nomeAplicativo = "Cookbook SwiftUI"

struct ContentView: View {
    var body: some View {
        Text(nomeAplicativo)
    }
}
```

Nesse exemplo, `nomeAplicativo` foi criado fora da `struct`, por isso pode ser acessado dentro da `ContentView`.

---

## 3. Escopo local

O escopo local acontece quando uma variável ou constante é criada dentro de um bloco de código.

Ela só pode ser usada dentro desse bloco.

```swift
func mostrarMensagem() {
    let mensagem = "Olá, Swift!"
    print(mensagem)
}
```

A constante `mensagem` só existe dentro da função `mostrarMensagem`.

Se tentarmos acessar fora da função, teremos erro:

```swift
func mostrarMensagem() {
    let mensagem = "Olá, Swift!"
    print(mensagem)
}

print(mensagem) // Erro
```

---

## 4. Escopo de função

Quando criamos uma variável dentro de uma função, ela pertence apenas àquela função.

```swift
func calcularMedia() {
    let nota1 = 8.0
    let nota2 = 9.0
    let media = (nota1 + nota2) / 2
    
    print(media)
}
```

As constantes `nota1`, `nota2` e `media` só podem ser usadas dentro da função `calcularMedia`.

---

## 5. Escopo de função em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    func gerarMensagem() -> String {
        let nome = "João"
        return "Olá, \(nome)!"
    }
    
    var body: some View {
        Text(gerarMensagem())
    }
}
```

Nesse exemplo:

- `gerarMensagem()` é uma função dentro da `ContentView`;
- `nome` existe apenas dentro da função;
- o `Text` consegue chamar a função, mas não consegue acessar diretamente a constante `nome`.

Exemplo incorreto:

```swift
import SwiftUI

struct ContentView: View {
    func gerarMensagem() -> String {
        let nome = "João"
        return "Olá, \(nome)!"
    }
    
    var body: some View {
        Text(nome) // Erro
    }
}
```

---

## 6. Escopo de struct

Em SwiftUI, uma tela geralmente é criada usando uma `struct`.

Tudo que é declarado dentro da `struct`, mas fora do `body`, pode ser usado dentro da tela.

```swift
import SwiftUI

struct ContentView: View {
    let titulo = "Página Inicial"
    
    var body: some View {
        Text(titulo)
    }
}
```

Nesse exemplo, `titulo` pertence ao escopo da `ContentView`.

---

## 7. Escopo do body

O `body` é a propriedade onde construímos a interface da tela.

```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        let mensagem = "Olá, SwiftUI!"
        
        Text(mensagem)
    }
}
```

Nesse exemplo, `mensagem` foi criada dentro do `body`, então só pode ser usada dentro dele.

Porém, em SwiftUI, é mais comum declarar propriedades fora do `body`, principalmente quando elas serão usadas em mais de um lugar.

Exemplo mais comum:

```swift
import SwiftUI

struct ContentView: View {
    let mensagem = "Olá, SwiftUI!"
    
    var body: some View {
        Text(mensagem)
    }
}
```

---

## 8. Escopo de bloco

Blocos são partes do código delimitadas por chaves `{ }`.

Exemplo com `if`:

```swift
let idade = 20

if idade >= 18 {
    let mensagem = "Maior de idade"
    print(mensagem)
}
```

A constante `mensagem` só existe dentro do bloco do `if`.

Exemplo incorreto:

```swift
let idade = 20

if idade >= 18 {
    let mensagem = "Maior de idade"
}

print(mensagem) // Erro
```

---

## 9. Escopo com if em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let idade = 20
    
    var body: some View {
        VStack {
            if idade >= 18 {
                let mensagem = "Maior de idade"
                Text(mensagem)
            }
        }
    }
}
```

Nesse exemplo, `mensagem` só pode ser usada dentro do bloco do `if`.

---

## 10. Escopo com else

Cada bloco possui seu próprio escopo.

```swift
let idade = 16

if idade >= 18 {
    let mensagem = "Maior de idade"
    print(mensagem)
} else {
    let mensagem = "Menor de idade"
    print(mensagem)
}
```

Nesse caso, existem duas constantes chamadas `mensagem`, mas cada uma pertence a um bloco diferente.

Resultado:

```txt
Menor de idade
```

---

## 11. Escopo com ForEach

No SwiftUI, o `ForEach` cria um escopo para cada item percorrido.

```swift
import SwiftUI

struct ContentView: View {
    let nomes = ["Marina", "João", "Bianca"]
    
    var body: some View {
        VStack {
            ForEach(nomes, id: \.self) { nome in
                Text(nome)
            }
        }
    }
}
```

Nesse exemplo:

- `nomes` pertence ao escopo da `ContentView`;
- `nome` existe apenas dentro do bloco do `ForEach`;
- cada item da lista é acessado temporariamente como `nome`.

Exemplo incorreto:

```swift
import SwiftUI

struct ContentView: View {
    let nomes = ["Marina", "João", "Bianca"]
    
    var body: some View {
        VStack {
            ForEach(nomes, id: \.self) { nome in
                Text(nome)
            }
            
            Text(nome) // Erro
        }
    }
}
```

---

## 12. Escopo com Button

O bloco de um `Button` também possui escopo próprio.

```swift
import SwiftUI

struct ContentView: View {
    @State private var contador = 0
    
    var body: some View {
        VStack(spacing: 16) {
            Text("Contador: \(contador)")
            
            Button("Aumentar") {
                let valor = 1
                contador += valor
            }
        }
    }
}
```

Nesse exemplo, `valor` só existe dentro do bloco do botão.

Exemplo incorreto:

```swift
import SwiftUI

struct ContentView: View {
    @State private var contador = 0
    
    var body: some View {
        VStack {
            Button("Aumentar") {
                let valor = 1
                contador += valor
            }
            
            Text("\(valor)") // Erro
        }
    }
}
```

---

## 13. Escopo e @State

No SwiftUI, variáveis com `@State` geralmente são declaradas dentro da `struct` e fora do `body`.

Isso permite que elas sejam acessadas por vários componentes da tela.

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Text("Olá, \(nome)!")
        }
        .padding()
    }
}
```

Nesse exemplo:

- `nome` pertence ao escopo da `ContentView`;
- o `TextField` consegue alterar `nome`;
- o `Text` consegue exibir `nome`;
- a tela atualiza quando `nome` muda.

---

## 14. Por que usar private?

É comum declarar `@State` com `private`.

```swift
@State private var nome = ""
```

O `private` significa que essa variável só pode ser acessada dentro da própria `struct`.

Isso ajuda a proteger o estado da tela e evita alterações externas indevidas.

Exemplo:

```swift
import SwiftUI

struct ContentView: View {
    @State private var contador = 0
    
    var body: some View {
        Button("Aumentar") {
            contador += 1
        }
    }
}
```

Nesse caso, `contador` pertence apenas à `ContentView`.

---

## 15. Escopo de propriedade

Uma propriedade é uma variável ou constante declarada dentro de uma `struct`, `class` ou `enum`.

```swift
struct Estudante {
    let nome: String
    let curso: String
}
```

Nesse exemplo, `nome` e `curso` são propriedades da struct `Estudante`.

Usando a struct:

```swift
let estudante = Estudante(nome: "Carlos", curso: "Programação")

print(estudante.nome)
print(estudante.curso)
```

Resultado:

```txt
Carlos
Programação
```

---

## 16. Escopo de propriedade em SwiftUI

```swift
import SwiftUI

struct Estudante {
    let nome: String
    let curso: String
}

struct ContentView: View {
    let estudante = Estudante(nome: "Carlos", curso: "Programação")
    
    var body: some View {
        VStack {
            Text(estudante.nome)
            Text(estudante.curso)
        }
    }
}
```

Nesse exemplo:

- `Estudante` é uma struct;
- `estudante` é uma propriedade da `ContentView`;
- `body` consegue acessar `estudante.nome` e `estudante.curso`.

---

## 17. Escopo de parâmetro

Parâmetros são valores recebidos por funções.

Eles só existem dentro da função onde foram declarados.

```swift
func cumprimentar(nome: String) {
    print("Olá, \(nome)!")
}
```

Nesse exemplo, `nome` é um parâmetro da função `cumprimentar`.

Ele só pode ser usado dentro da função.

```swift
cumprimentar(nome: "Amanda")
```

Resultado:

```txt
Olá, Amanda!
```

---

## 18. Escopo de parâmetro em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    func gerarMensagem(nome: String) -> String {
        return "Olá, \(nome)!"
    }
    
    var body: some View {
        Text(gerarMensagem(nome: "Amanda"))
    }
}
```

Nesse exemplo:

- `nome` é um parâmetro da função `gerarMensagem`;
- ele só existe dentro da função;
- ao chamar a função, passamos o valor `"Amanda"`.

---

## 19. Shadowing

Shadowing acontece quando uma variável local tem o mesmo nome de uma variável de um escopo externo.

```swift
let nome = "Marina"

func mostrarNome() {
    let nome = "João"
    print(nome)
}

mostrarNome()
```

Resultado:

```txt
João
```

Nesse exemplo:

- existe um `nome` no escopo externo com valor `"Marina"`;
- existe outro `nome` dentro da função com valor `"João"`;
- dentro da função, o Swift usa o `nome` mais próximo.

Apesar de funcionar, é melhor evitar nomes repetidos quando isso deixa o código confuso.

---

## 20. Shadowing em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let nome = "Marina"
    
    var body: some View {
        VStack {
            let nome = "João"
            Text(nome)
        }
    }
}
```

Resultado:

```txt
João
```

Nesse exemplo, o `nome` criado dentro do `VStack` tem prioridade dentro daquele bloco.

Para evitar confusão, prefira nomes mais claros:

```swift
let nomeUsuario = "Marina"
let nomeExibido = "João"
```

---

## 21. Escopo e variáveis temporárias

Variáveis temporárias são úteis quando precisamos calcular ou preparar algum valor dentro de um bloco.

```swift
func calcularDesconto(preco: Double) -> Double {
    let desconto = preco * 0.10
    let precoFinal = preco - desconto
    
    return precoFinal
}
```

Nesse exemplo:

- `desconto` só existe dentro da função;
- `precoFinal` só existe dentro da função;
- o valor retornado é usado fora dela.

---

## 22. Escopo e funções auxiliares

Em SwiftUI, podemos criar funções auxiliares dentro da `struct` para organizar melhor o código.

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    @State private var mensagem = ""
    
    func confirmar() {
        if nome.isEmpty {
            mensagem = "Digite um nome"
        } else {
            mensagem = "Cadastro confirmado para \(nome)"
        }
    }
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
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

- `nome` e `mensagem` pertencem ao escopo da `ContentView`;
- a função `confirmar()` também pertence à `ContentView`;
- o botão consegue chamar `confirmar()`;
- a função consegue acessar e alterar as variáveis de estado.

---

## 23. Escopo com computed property

Uma **computed property** é uma propriedade calculada.

Ela não armazena um valor fixo, mas calcula um resultado quando é acessada.

```swift
import SwiftUI

struct ContentView: View {
    @State private var idade = 18
    
    var maiorDeIdade: Bool {
        idade >= 18
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Stepper("Idade: \(idade)", value: $idade, in: 0...100)
            
            Text(maiorDeIdade ? "Maior de idade" : "Menor de idade")
        }
        .padding()
    }
}
```

Nesse exemplo:

- `idade` pertence ao escopo da `ContentView`;
- `maiorDeIdade` também pertence à `ContentView`;
- `maiorDeIdade` calcula um `Bool` com base na idade;
- o `Text` usa esse valor calculado.

---

## 24. Diferença entre variável local e propriedade

| Tipo | Onde é declarada | Onde pode ser usada |
|---|---|---|
| Variável local | Dentro de função ou bloco | Apenas dentro daquele bloco |
| Propriedade | Dentro da struct, fora do body | Dentro da struct inteira |
| Global | Fora de structs e funções | Em várias partes do arquivo |
| Parâmetro | Dentro da declaração de função | Apenas dentro da função |

Exemplo de variável local:

```swift
func exemplo() {
    let mensagem = "Olá"
    print(mensagem)
}
```

Exemplo de propriedade:

```swift
struct ContentView: View {
    let mensagem = "Olá"
    
    var body: some View {
        Text(mensagem)
    }
}
```

---

## 25. Exemplo completo

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    @State private var idade = 18
    @State private var mensagem = ""
    
    var maiorDeIdade: Bool {
        idade >= 18
    }
    
    func confirmarCadastro() {
        let nomeTratado = nome.trimmingCharacters(in: .whitespaces)
        
        if nomeTratado.isEmpty {
            mensagem = "Digite um nome válido"
        } else if maiorDeIdade {
            mensagem = "Cadastro permitido para \(nomeTratado)"
        } else {
            mensagem = "Cadastro bloqueado para \(nomeTratado)"
        }
    }
    
    var body: some View {
        VStack(spacing: 20) {
            Text("Escopos em SwiftUI")
                .font(.title2)
                .bold()
            
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Stepper("Idade: \(idade)", value: $idade, in: 0...100)
            
            Text(maiorDeIdade ? "Maior de idade" : "Menor de idade")
            
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

Nesse exemplo:

- `nome`, `idade` e `mensagem` pertencem ao escopo da `ContentView`;
- `maiorDeIdade` é uma propriedade calculada;
- `confirmarCadastro()` é uma função da `ContentView`;
- `nomeTratado` é uma constante local da função;
- `body` monta a interface e acessa as propriedades da tela.

---

## 26. Resumo dos escopos

| Escopo | Descrição | Exemplo |
|---|---|---|
| Global | Fora de structs e funções | `let appName = "Cookbook"` |
| Struct | Dentro da struct | `let titulo = "Home"` |
| Body | Dentro do `body` | `let mensagem = "Olá"` |
| Função | Dentro de uma função | `let resultado = 10 + 5` |
| Bloco | Dentro de `{ }` | `if idade >= 18 { ... }` |
| Parâmetro | Dentro da função que recebe o valor | `func ola(nome: String)` |

---

## Pontos-chave

- Escopo define onde uma variável, constante ou função pode ser acessada.
- Em Swift, escopos são delimitados por chaves `{ }`.
- Variáveis locais só existem dentro do bloco onde foram criadas.
- Propriedades declaradas dentro da `struct` podem ser usadas no `body` e em funções da mesma `struct`.
- Variáveis com `@State` geralmente ficam no escopo da `struct`.
- O `private` limita o acesso à própria estrutura.
- Parâmetros de função só existem dentro da função.
- `ForEach`, `Button`, `if`, `else` e funções criam seus próprios escopos.
- Shadowing acontece quando uma variável local tem o mesmo nome de uma variável externa.
- Entender escopo ajuda a evitar erros como “variável não encontrada”.

---

## Desafio

Crie uma tela em SwiftUI com:

- uma variável de estado `nome`;
- uma variável de estado `idade`;
- uma propriedade calculada chamada `maiorDeIdade`;
- uma função chamada `gerarMensagem`;
- uma variável local dentro da função;
- um botão para exibir a mensagem final.

Exemplo esperado:

```txt
Nome: Amanda
Idade: 20
Maior de idade
Cadastro permitido para Amanda
```