# Closures em SwiftUI

Em programação, **closures** são blocos de código que podem ser armazenados, passados como parâmetro e executados depois.

Em Swift, closures aparecem com muita frequência.

No SwiftUI, usamos closures o tempo todo, principalmente em componentes como `Button`, `ForEach`, `List`, `filter`, `map`, `sorted` e ações de tela.

---

## 1. O que são closures?

Uma closure é como uma função, mas sem precisar declarar um nome.

Exemplo de função:

```swift
func cumprimentar() {
    print("Olá, Swift!")
}

cumprimentar()
```

Exemplo parecido usando closure:

```swift
let cumprimentar = {
    print("Olá, Swift!")
}

cumprimentar()
```

Resultado:

```txt
Olá, Swift!
```

Nesse exemplo:

- a closure foi armazenada na constante `cumprimentar`;
- depois, ela foi executada usando `cumprimentar()`.

---

## 2. Closure simples

Uma closure pode executar uma ação simples.

```swift
let mensagem = {
    print("Bem-vindo ao SwiftUI!")
}

mensagem()
```

Resultado:

```txt
Bem-vindo ao SwiftUI!
```

---

## 3. Closure com parâmetro

Closures também podem receber parâmetros.

```swift
let cumprimentar = { (nome: String) in
    print("Olá, \(nome)!")
}

cumprimentar("Marina")
```

Resultado:

```txt
Olá, Marina!
```

Nesse exemplo:

- `nome` é o parâmetro da closure;
- `String` é o tipo do parâmetro;
- `in` separa os parâmetros do corpo da closure.

---

## 4. Entendendo o in

Em uma closure, usamos `in` para separar a parte dos parâmetros da parte do código que será executado.

```swift
let somar = { (numero1: Int, numero2: Int) in
    return numero1 + numero2
}
```

A parte antes do `in` define os dados que a closure recebe:

```swift
(numero1: Int, numero2: Int)
```

A parte depois do `in` define o que a closure faz:

```swift
return numero1 + numero2
```

---

## 5. Closure com retorno

Uma closure pode retornar um valor.

```swift
let somar = { (numero1: Int, numero2: Int) -> Int in
    return numero1 + numero2
}

let resultado = somar(10, 5)

print(resultado)
```

Resultado:

```txt
15
```

---

## 6. Closure com inferência de tipo

O Swift consegue entender muitos tipos automaticamente.

```swift
let multiplicar: (Int, Int) -> Int = { numero1, numero2 in
    return numero1 * numero2
}

let resultado = multiplicar(4, 3)

print(resultado)
```

Resultado:

```txt
12
```

Nesse exemplo:

```swift
(Int, Int) -> Int
```

significa que a closure:

- recebe dois valores `Int`;
- retorna um valor `Int`.

---

## 7. Closure sem retorno

Quando uma closure não retorna nada, o retorno é `Void`.

```swift
let exibirMensagem: () -> Void = {
    print("Mensagem exibida!")
}

exibirMensagem()
```

Resultado:

```txt
Mensagem exibida!
```

Esse tipo:

```swift
() -> Void
```

significa que a closure:

- não recebe parâmetro;
- não retorna valor.

---

## 8. Closure como parâmetro de função

Uma função pode receber uma closure como parâmetro.

```swift
func executarAcao(acao: () -> Void) {
    acao()
}

executarAcao {
    print("Ação executada!")
}
```

Resultado:

```txt
Ação executada!
```

Nesse exemplo:

- `executarAcao` recebe uma closure chamada `acao`;
- dentro da função, a closure é executada com `acao()`;
- ao chamar a função, passamos o bloco de código que será executado.

---

## 9. Closure com parâmetro em função

```swift
func processarNome(nome: String, acao: (String) -> Void) {
    acao(nome)
}

processarNome(nome: "João") { nomeRecebido in
    print("Nome recebido: \(nomeRecebido)")
}
```

Resultado:

```txt
Nome recebido: João
```

Nesse exemplo:

- a função recebe um nome;
- também recebe uma closure;
- a closure recebe uma `String`;
- a função chama a closure passando o nome.

---

## 10. Closure com retorno em função

```swift
func calcular(numero1: Int, numero2: Int, operacao: (Int, Int) -> Int) -> Int {
    return operacao(numero1, numero2)
}

let resultado = calcular(numero1: 10, numero2: 5) { valor1, valor2 in
    return valor1 + valor2
}

print(resultado)
```

Resultado:

```txt
15
```

Nesse exemplo:

- a função `calcular` recebe dois números;
- também recebe uma closure chamada `operacao`;
- a closure decide qual cálculo será feito.

---

## 11. Closure no Button

No SwiftUI, o `Button` usa closure para definir o que acontece quando ele é clicado.

```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        Button("Clique aqui") {
            print("Botão clicado")
        }
    }
}
```

Nesse exemplo, este bloco é uma closure:

```swift
{
    print("Botão clicado")
}
```

Ela representa a ação do botão.

---

## 12. Closure no Button com @State

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
        }
        .padding()
    }
}
```

Nesse exemplo:

- o botão recebe uma closure;
- dentro da closure, `contador` é aumentado;
- como `contador` usa `@State`, a tela atualiza automaticamente.

---

## 13. Closure no ForEach

O `ForEach` usa closure para definir como cada item será exibido.

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

Neste trecho:

```swift
{ nome in
    Text(nome)
}
```

a closure recebe cada item do array e retorna uma `View`.

---

## 14. Closure no List

```swift
import SwiftUI

struct ContentView: View {
    let cursos = ["Design", "Programação", "Inovação"]
    
    var body: some View {
        List(cursos, id: \.self) { curso in
            Text(curso)
        }
    }
}
```

Nesse exemplo:

- `List` percorre o array `cursos`;
- para cada item, a closure cria um `Text`.

---

## 15. Closure com filter

O método `.filter` usa uma closure para decidir quais itens permanecem na lista.

```swift
let notas = [8.0, 5.5, 9.0, 6.0]

let aprovadas = notas.filter { nota in
    nota >= 7
}

print(aprovadas)
```

Resultado:

```txt
[8.0, 9.0]
```

Nesse exemplo:

- a closure recebe cada `nota`;
- se `nota >= 7` for verdadeiro, a nota entra no novo array.

---

## 16. Closure com map

O método `.map` usa uma closure para transformar os itens de uma coleção.

```swift
let nomes = ["marina", "joão", "bianca"]

let nomesMaiusculos = nomes.map { nome in
    nome.uppercased()
}

print(nomesMaiusculos)
```

Resultado:

```txt
["MARINA", "JOÃO", "BIANCA"]
```

Nesse exemplo:

- a closure recebe cada nome;
- transforma cada nome em letras maiúsculas;
- retorna um novo array.

---

## 17. Closure com sorted

O método `.sorted` pode usar uma closure para definir a ordem dos itens.

```swift
let nomes = ["Bianca", "Amanda", "Carlos"]

let nomesOrdenados = nomes.sorted { primeiro, segundo in
    primeiro < segundo
}

print(nomesOrdenados)
```

Resultado:

```txt
["Amanda", "Bianca", "Carlos"]
```

Nesse exemplo:

- a closure recebe dois valores;
- compara os dois;
- define a ordem da lista.

---

## 18. Sintaxe curta com $0

Swift permite escrever closures de forma mais curta usando `$0`, `$1`, `$2` e assim por diante.

Exemplo comum:

```swift
let notas = [8.0, 5.5, 9.0, 6.0]

let aprovadas = notas.filter {
    $0 >= 7
}

print(aprovadas)
```

Resultado:

```txt
[8.0, 9.0]
```

Nesse caso:

```swift
$0
```

representa o primeiro parâmetro da closure.

---

## 19. Sintaxe curta com dois parâmetros

Quando a closure recebe dois parâmetros, usamos `$0` e `$1`.

```swift
let numeros = [3, 1, 4, 2]

let ordenados = numeros.sorted {
    $0 < $1
}

print(ordenados)
```

Resultado:

```txt
[1, 2, 3, 4]
```

Nesse exemplo:

- `$0` representa o primeiro número;
- `$1` representa o segundo número.

---

## 20. Comparando sintaxe completa e curta

Sintaxe completa:

```swift
let aprovadas = notas.filter { nota in
    nota >= 7
}
```

Sintaxe curta:

```swift
let aprovadas = notas.filter {
    $0 >= 7
}
```

As duas fazem a mesma coisa.

Para quem está começando, a sintaxe completa costuma ser mais fácil de entender.

---

## 21. Trailing closure

Quando uma função recebe uma closure como último parâmetro, podemos escrevê-la fora dos parênteses.

Exemplo com parênteses:

```swift
Button("Enviar", action: {
    print("Enviado")
})
```

Exemplo com trailing closure:

```swift
Button("Enviar") {
    print("Enviado")
}
```

No SwiftUI, essa segunda forma é a mais comum.

---

## 22. Trailing closure no SwiftUI

Vários componentes do SwiftUI usam trailing closures.

```swift
VStack {
    Text("Título")
    Text("Descrição")
}
```

Nesse exemplo, o bloco dentro de `VStack` é uma closure que retorna várias views.

Outro exemplo:

```swift
List(cursos, id: \.self) { curso in
    Text(curso)
}
```

A closure define o conteúdo da lista.

---

## 23. Closures e ações

Closures são muito usadas para passar ações de uma View para outra.

```swift
import SwiftUI

struct BotaoPersonalizado: View {
    let titulo: String
    let acao: () -> Void
    
    var body: some View {
        Button(titulo) {
            acao()
        }
    }
}

struct ContentView: View {
    @State private var contador = 0
    
    var body: some View {
        VStack(spacing: 16) {
            Text("Contador: \(contador)")
            
            BotaoPersonalizado(titulo: "Aumentar") {
                contador += 1
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- `BotaoPersonalizado` recebe uma closure chamada `acao`;
- a `ContentView` define o que essa ação faz;
- ao clicar no botão, a closure é executada.

---

## 24. Closure com parâmetro em uma View

Uma View também pode receber uma closure com parâmetro.

```swift
import SwiftUI

struct ItemLista: View {
    let nome: String
    let aoSelecionar: (String) -> Void
    
    var body: some View {
        Button(nome) {
            aoSelecionar(nome)
        }
    }
}

struct ContentView: View {
    @State private var mensagem = ""
    
    let nomes = ["Marina", "João", "Bianca"]
    
    var body: some View {
        VStack(spacing: 16) {
            ForEach(nomes, id: \.self) { nome in
                ItemLista(nome: nome) { nomeSelecionado in
                    mensagem = "Selecionado: \(nomeSelecionado)"
                }
            }
            
            Text(mensagem)
        }
        .padding()
    }
}
```

Nesse exemplo:

- `ItemLista` recebe uma closure chamada `aoSelecionar`;
- quando o botão é clicado, ela envia o nome selecionado;
- a `ContentView` recebe esse nome e atualiza a mensagem.

---

## 25. Closure com retorno em uma View

Também podemos usar closures que retornam valores.

```swift
import SwiftUI

struct CartaoEstudante: View {
    let nome: String
    let gerarDescricao: (String) -> String
    
    var body: some View {
        VStack(alignment: .leading) {
            Text(nome)
                .font(.headline)
            
            Text(gerarDescricao(nome))
                .font(.subheadline)
        }
        .padding()
    }
}

struct ContentView: View {
    var body: some View {
        CartaoEstudante(nome: "Carlos") { nome in
            return "\(nome) está estudando SwiftUI."
        }
    }
}
```

Nesse exemplo:

- `CartaoEstudante` recebe uma closure;
- essa closure recebe um nome;
- retorna uma descrição em `String`.

---

## 26. Captura de valores

Closures podem capturar valores do escopo onde foram criadas.

```swift
var contador = 0

let aumentar = {
    contador += 1
    print(contador)
}

aumentar()
aumentar()
```

Resultado:

```txt
1
2
```

Nesse exemplo, a closure `aumentar` consegue acessar e modificar `contador`.

---

## 27. Captura de valores no SwiftUI

No SwiftUI, closures capturam valores com frequência.

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

A closure do botão consegue acessar `contador`, que pertence à `ContentView`.

---

## 28. Closure assíncrona

Em Swift, também podemos usar closures com tarefas assíncronas.

```swift
func buscarDados(conclusao: @escaping (String) -> Void) {
    DispatchQueue.main.asyncAfter(deadline: .now() + 2) {
        conclusao("Dados carregados")
    }
}
```

Usando a função:

```swift
buscarDados { resultado in
    print(resultado)
}
```

Resultado depois de alguns segundos:

```txt
Dados carregados
```

O `@escaping` indica que a closure pode ser executada depois que a função terminar.

---

## 29. Closure assíncrona em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    @State private var mensagem = "Carregando..."
    
    func buscarDados(conclusao: @escaping (String) -> Void) {
        DispatchQueue.main.asyncAfter(deadline: .now() + 2) {
            conclusao("Dados carregados com sucesso")
        }
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Text(mensagem)
            
            Button("Buscar dados") {
                buscarDados { resultado in
                    mensagem = resultado
                }
            }
        }
        .padding()
    }
}
```

Nesse exemplo:

- o botão chama `buscarDados`;
- a closure será executada depois de 2 segundos;
- quando termina, ela atualiza `mensagem`.

---

## 30. Exemplo completo

```swift
import SwiftUI

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
    let nota: Double
}

struct BotaoAcao: View {
    let titulo: String
    let acao: () -> Void
    
    var body: some View {
        Button(titulo) {
            acao()
        }
        .buttonStyle(.borderedProminent)
    }
}

struct ContentView: View {
    @State private var estudantes = [
        Estudante(nome: "Marina", nota: 8.5),
        Estudante(nome: "João", nota: 6.0),
        Estudante(nome: "Bianca", nota: 9.0),
        Estudante(nome: "Carlos", nota: 5.5)
    ]
    
    @State private var mensagem = ""
    
    var aprovados: [Estudante] {
        estudantes.filter { estudante in
            estudante.nota >= 7
        }
    }
    
    var ordenadosPorNome: [Estudante] {
        estudantes.sorted { primeiro, segundo in
            primeiro.nome < segundo.nome
        }
    }
    
    var body: some View {
        NavigationStack {
            VStack(spacing: 16) {
                List {
                    Section("Todos") {
                        ForEach(ordenadosPorNome) { estudante in
                            Button {
                                mensagem = "\(estudante.nome) selecionado"
                            } label: {
                                HStack {
                                    Text(estudante.nome)
                                    Spacer()
                                    Text(String(format: "%.1f", estudante.nota))
                                }
                            }
                        }
                    }
                    
                    Section("Aprovados") {
                        ForEach(aprovados) { estudante in
                            Text(estudante.nome)
                        }
                    }
                }
                
                Text(mensagem)
                
                BotaoAcao(titulo: "Adicionar Amanda") {
                    estudantes.append(
                        Estudante(nome: "Amanda", nota: 7.5)
                    )
                }
            }
            .navigationTitle("Closures")
        }
    }
}
```

Nesse exemplo:

- `Button` usa closure para executar ações;
- `ForEach` usa closure para montar os itens da lista;
- `filter` usa closure para filtrar aprovados;
- `sorted` usa closure para ordenar estudantes;
- `BotaoAcao` recebe uma closure como propriedade;
- a tela atualiza quando a lista muda.

---

## 31. Resumo das closures

| Conceito | Exemplo |
|---|---|
| Closure simples | `{ print("Olá") }` |
| Closure com parâmetro | `{ nome in print(nome) }` |
| Closure com retorno | `{ numero in return numero * 2 }` |
| Sintaxe curta | `{ $0 >= 7 }` |
| Trailing closure | `Button("Enviar") { ... }` |
| Closure como parâmetro | `let acao: () -> Void` |
| Closure com retorno | `(String) -> String` |
| Closure assíncrona | `@escaping (String) -> Void` |

---

## Pontos-chave

- Closures são blocos de código reutilizáveis.
- Closures podem ser armazenadas em variáveis ou constantes.
- Closures podem receber parâmetros.
- Closures podem retornar valores.
- O `in` separa os parâmetros do corpo da closure.
- Swift permite sintaxe curta com `$0`, `$1`, `$2`.
- Trailing closure é muito usada em SwiftUI.
- `Button`, `ForEach`, `List`, `filter`, `map` e `sorted` usam closures.
- Closures podem capturar valores do escopo onde foram criadas.
- `@escaping` é usado quando a closure pode ser executada depois que a função termina.

---

## Desafio

Crie uma tela em SwiftUI com:

- uma struct chamada `Produto`;
- os campos `nome`, `preco` e `categoria`;
- uma lista de produtos;
- uma computed property usando `filter` para mostrar produtos acima de R$ 100;
- uma computed property usando `sorted` para ordenar por nome;
- um botão personalizado que receba uma closure;
- uma mensagem que mude ao clicar em um produto.

Exemplo esperado:

```txt
Produtos

Mouse - R$ 80.00
Teclado - R$ 150.00
Monitor - R$ 900.00

Produtos acima de R$ 100

Monitor
Teclado

Selecionado: Monitor
```