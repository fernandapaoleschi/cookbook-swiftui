# Laços de Repetição em SwiftUI

Em programação, **laços de repetição** são estruturas usadas para executar um bloco de código várias vezes.

No Swift, os principais laços são:

| Laço | Uso |
|---|---|
| `for` | Percorrer sequências, arrays e intervalos |
| `while` | Repetir enquanto uma condição for verdadeira |
| `repeat while` | Executar pelo menos uma vez e depois repetir enquanto a condição for verdadeira |

No SwiftUI, o laço mais usado é o `ForEach`, porque ele permite exibir listas de elementos na interface.

---

## 1. O que são laços de repetição?

Laços de repetição evitam que a gente precise escrever o mesmo código várias vezes.

Exemplo sem laço:

```swift
print("Marina")
print("João")
print("Bianca")
```

Exemplo com laço:

```swift
let nomes = ["Marina", "João", "Bianca"]

for nome in nomes {
    print(nome)
}
```

Resultado:

```txt
Marina
João
Bianca
```

---

## 2. For

O `for` é usado para percorrer uma sequência de valores.

### Sintaxe

```swift
for item in colecao {
    // Código repetido para cada item
}
```

### Exemplo

```swift
let cursos = ["Design", "Programação", "Inovação"]

for curso in cursos {
    print(curso)
}
```

Resultado:

```txt
Design
Programação
Inovação
```

Nesse exemplo:

- `cursos` é a coleção;
- `curso` representa cada item da coleção;
- o `print(curso)` é executado para cada item.

---

## 3. For com Array

O `for` é muito usado com arrays.

```swift
let estudantes = ["Carlos", "Amanda", "Lucas"]

for estudante in estudantes {
    print("Estudante: \(estudante)")
}
```

Resultado:

```txt
Estudante: Carlos
Estudante: Amanda
Estudante: Lucas
```

---

## 4. For com números

Também podemos usar `for` com intervalos numéricos.

```swift
for numero in 1...5 {
    print(numero)
}
```

Resultado:

```txt
1
2
3
4
5
```

O operador `...` cria um intervalo fechado, incluindo o primeiro e o último valor.

---

## 5. Intervalo semiaberto

O operador `..<` cria um intervalo que não inclui o último valor.

```swift
for numero in 1..<5 {
    print(numero)
}
```

Resultado:

```txt
1
2
3
4
```

Nesse caso, o número `5` não entra na repetição.

---

## 6. For com índice

Às vezes, precisamos acessar o índice e o valor ao mesmo tempo.

```swift
let nomes = ["Marina", "João", "Bianca"]

for (indice, nome) in nomes.enumerated() {
    print("\(indice): \(nome)")
}
```

Resultado:

```txt
0: Marina
1: João
2: Bianca
```

O método `.enumerated()` permite percorrer o array trazendo o índice e o valor.

---

## 7. For com condição

Podemos usar `if` dentro de um `for`.

```swift
let notas = [8.0, 5.5, 9.0, 6.0]

for nota in notas {
    if nota >= 7 {
        print("Aprovado com nota \(nota)")
    } else {
        print("Reprovado com nota \(nota)")
    }
}
```

Resultado:

```txt
Aprovado com nota 8.0
Reprovado com nota 5.5
Aprovado com nota 9.0
Reprovado com nota 6.0
```

---

## 8. ForEach em SwiftUI

No SwiftUI, usamos `ForEach` para repetir componentes visuais.

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

Resultado exibido na tela:

```txt
Marina
João
Bianca
```

Nesse exemplo:

- `ForEach` percorre o array `nomes`;
- cada item é representado por `nome`;
- para cada nome, um `Text` é criado.

---

## 9. ForEach com intervalo

Também podemos usar `ForEach` com intervalos numéricos.

```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            ForEach(1...5, id: \.self) { numero in
                Text("Item \(numero)")
            }
        }
    }
}
```

Resultado:

```txt
Item 1
Item 2
Item 3
Item 4
Item 5
```

---

## 10. ForEach com List

O `ForEach` é muito usado dentro de `List`.

```swift
import SwiftUI

struct ContentView: View {
    let cursos = ["Design", "Programação", "Inovação"]
    
    var body: some View {
        List {
            ForEach(cursos, id: \.self) { curso in
                Text(curso)
            }
        }
    }
}
```

Nesse exemplo, cada curso aparece como um item da lista.

---

## 11. List sem ForEach

Quando a lista é simples, também podemos passar o array direto para a `List`.

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

Esse código tem o mesmo resultado do exemplo anterior, mas é mais curto.

---

## 12. ForEach com Struct

Em projetos reais, geralmente usamos `ForEach` com uma lista de structs.

```swift
struct Estudante {
    let nome: String
    let curso: String
}
```

Criando os dados:

```swift
let estudantes = [
    Estudante(nome: "Marina", curso: "Design"),
    Estudante(nome: "João", curso: "Programação"),
    Estudante(nome: "Bianca", curso: "Inovação")
]
```

---

## 13. ForEach com Identifiable

Para o SwiftUI identificar cada item da lista, podemos usar `Identifiable`.

```swift
import SwiftUI

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
    let curso: String
}

struct ContentView: View {
    let estudantes = [
        Estudante(nome: "Marina", curso: "Design"),
        Estudante(nome: "João", curso: "Programação"),
        Estudante(nome: "Bianca", curso: "Inovação")
    ]
    
    var body: some View {
        List {
            ForEach(estudantes) { estudante in
                VStack(alignment: .leading) {
                    Text(estudante.nome)
                        .font(.headline)
                    
                    Text(estudante.curso)
                        .font(.subheadline)
                }
            }
        }
    }
}
```

Nesse exemplo:

- `Estudante` segue o protocolo `Identifiable`;
- cada estudante recebe um `id`;
- o SwiftUI consegue diferenciar os itens da lista.

---

## 14. ForEach com Cards

O `ForEach` também pode ser usado para criar cards repetidos.

```swift
import SwiftUI

struct Curso: Identifiable {
    let id = UUID()
    let nome: String
    let descricao: String
}

struct ContentView: View {
    let cursos = [
        Curso(nome: "Design", descricao: "Criação de interfaces e experiências"),
        Curso(nome: "Programação", descricao: "Desenvolvimento de aplicativos"),
        Curso(nome: "Inovação", descricao: "Criação de soluções criativas")
    ]
    
    var body: some View {
        VStack(spacing: 12) {
            ForEach(cursos) { curso in
                VStack(alignment: .leading, spacing: 6) {
                    Text(curso.nome)
                        .font(.headline)
                    
                    Text(curso.descricao)
                        .font(.subheadline)
                }
                .padding()
                .frame(maxWidth: .infinity, alignment: .leading)
                .background(.gray.opacity(0.15))
                .clipShape(RoundedRectangle(cornerRadius: 12))
            }
        }
        .padding()
    }
}
```

Nesse exemplo, cada curso vira um card na tela.

---

## 15. ForEach com @State

Podemos usar `@State` para alterar uma lista e atualizar a tela.

```swift
import SwiftUI

struct ContentView: View {
    @State private var nomes = ["Marina", "João"]
    
    var body: some View {
        VStack(spacing: 16) {
            List(nomes, id: \.self) { nome in
                Text(nome)
            }
            
            Button("Adicionar Bianca") {
                nomes.append("Bianca")
            }
        }
    }
}
```

Nesse exemplo:

- `nomes` começa com dois itens;
- ao clicar no botão, `"Bianca"` é adicionada;
- a lista atualiza automaticamente.

---

## 16. Removendo itens com ForEach

Podemos usar `.onDelete` para remover itens de uma lista.

```swift
import SwiftUI

struct ContentView: View {
    @State private var nomes = ["Marina", "João", "Bianca"]
    
    var body: some View {
        NavigationStack {
            List {
                ForEach(nomes, id: \.self) { nome in
                    Text(nome)
                }
                .onDelete { indexSet in
                    nomes.remove(atOffsets: indexSet)
                }
            }
            .navigationTitle("Nomes")
        }
    }
}
```

Nesse exemplo, o usuário pode arrastar um item para o lado e apagar.

---

## 17. While

O `while` executa um bloco de código enquanto uma condição for verdadeira.

### Sintaxe

```swift
while condição {
    // Código repetido
}
```

### Exemplo

```swift
var contador = 1

while contador <= 5 {
    print(contador)
    contador += 1
}
```

Resultado:

```txt
1
2
3
4
5
```

Nesse exemplo:

- `contador` começa em `1`;
- enquanto `contador <= 5`, o código continua repetindo;
- a cada repetição, `contador` aumenta em `1`.

---

## 18. Cuidado com loop infinito

Um loop infinito acontece quando a condição nunca fica falsa.

Exemplo perigoso:

```swift
var contador = 1

while contador <= 5 {
    print(contador)
}
```

Nesse exemplo, o valor de `contador` nunca muda, então o laço nunca termina.

Forma correta:

```swift
var contador = 1

while contador <= 5 {
    print(contador)
    contador += 1
}
```

---

## 19. While em SwiftUI

No SwiftUI, `while` não é usado diretamente para criar elementos visuais.

Para repetir elementos na tela, prefira `ForEach`.

Use `while` mais em funções, cálculos ou regras internas.

```swift
func contarAteCinco() {
    var contador = 1
    
    while contador <= 5 {
        print(contador)
        contador += 1
    }
}
```

Exemplo em SwiftUI:

```swift
import SwiftUI

struct ContentView: View {
    @State private var resultado = ""
    
    func gerarContagem() {
        var contador = 1
        var texto = ""
        
        while contador <= 5 {
            texto += "\(contador)\n"
            contador += 1
        }
        
        resultado = texto
    }
    
    var body: some View {
        VStack(spacing: 16) {
            Button("Gerar contagem") {
                gerarContagem()
            }
            
            Text(resultado)
        }
        .padding()
    }
}
```

---

## 20. Repeat While

O `repeat while` executa o código pelo menos uma vez antes de verificar a condição.

### Sintaxe

```swift
repeat {
    // Código executado pelo menos uma vez
} while condição
```

### Exemplo

```swift
var contador = 1

repeat {
    print(contador)
    contador += 1
} while contador <= 5
```

Resultado:

```txt
1
2
3
4
5
```

---

## 21. Diferença entre while e repeat while

No `while`, a condição é verificada antes da execução.

```swift
var numero = 10

while numero < 5 {
    print(numero)
}
```

Nesse caso, nada será exibido, porque `numero < 5` já começa falso.

No `repeat while`, o código executa pelo menos uma vez.

```swift
var numero = 10

repeat {
    print(numero)
} while numero < 5
```

Resultado:

```txt
10
```

---

## 22. Break

O `break` encerra um laço antes do fim.

```swift
for numero in 1...10 {
    if numero == 5 {
        break
    }
    
    print(numero)
}
```

Resultado:

```txt
1
2
3
4
```

Quando `numero` chega em `5`, o laço é interrompido.

---

## 23. Continue

O `continue` pula uma repetição e segue para a próxima.

```swift
for numero in 1...5 {
    if numero == 3 {
        continue
    }
    
    print(numero)
}
```

Resultado:

```txt
1
2
4
5
```

Quando `numero` é `3`, o `print` é pulado.

---

## 24. ForEach com filtro

No SwiftUI, em vez de usar `continue`, é comum filtrar os dados antes de exibir.

```swift
import SwiftUI

struct ContentView: View {
    let notas = [8.0, 5.5, 9.0, 6.0]
    
    var notasAprovadas: [Double] {
        notas.filter { nota in
            nota >= 7
        }
    }
    
    var body: some View {
        VStack {
            ForEach(notasAprovadas, id: \.self) { nota in
                Text("Nota aprovada: \(nota)")
            }
        }
    }
}
```

Resultado:

```txt
Nota aprovada: 8.0
Nota aprovada: 9.0
```

---

## 25. ForEach com map

O método `.map` transforma os itens de uma coleção.

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

---

## 26. ForEach com filter

O método `.filter` retorna apenas os itens que atendem a uma condição.

```swift
let idades = [16, 18, 20, 14, 22]

let maioresDeIdade = idades.filter { idade in
    idade >= 18
}

print(maioresDeIdade)
```

Resultado:

```txt
[18, 20, 22]
```

---

## 27. ForEach com sorted

O método `.sorted()` ordena os itens.

```swift
let nomes = ["Bianca", "Amanda", "Carlos"]

let nomesOrdenados = nomes.sorted()

print(nomesOrdenados)
```

Resultado:

```txt
["Amanda", "Bianca", "Carlos"]
```

---

## 28. Map, filter e sorted em SwiftUI

```swift
import SwiftUI

struct ContentView: View {
    let estudantes = ["Bianca", "Amanda", "Carlos", "João"]
    
    var estudantesFiltrados: [String] {
        estudantes
            .filter { $0.count >= 5 }
            .sorted()
    }
    
    var body: some View {
        List(estudantesFiltrados, id: \.self) { estudante in
            Text(estudante.uppercased())
        }
    }
}
```

Nesse exemplo:

- `.filter` mantém apenas nomes com 5 letras ou mais;
- `.sorted` ordena em ordem alfabética;
- `.uppercased()` transforma o texto em maiúsculo;
- a `List` exibe o resultado.

---

## 29. Exemplo completo

```swift
import SwiftUI

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
    let nota: Double
}

struct ContentView: View {
    @State private var estudantes = [
        Estudante(nome: "Marina", nota: 8.5),
        Estudante(nome: "João", nota: 6.0),
        Estudante(nome: "Bianca", nota: 9.0),
        Estudante(nome: "Carlos", nota: 5.5)
    ]
    
    var aprovados: [Estudante] {
        estudantes
            .filter { estudante in
                estudante.nota >= 7
            }
            .sorted { primeiro, segundo in
                primeiro.nome < segundo.nome
            }
    }
    
    var body: some View {
        NavigationStack {
            List {
                Section("Todos os estudantes") {
                    ForEach(estudantes) { estudante in
                        HStack {
                            Text(estudante.nome)
                            Spacer()
                            Text(String(format: "%.1f", estudante.nota))
                        }
                    }
                }
                
                Section("Aprovados") {
                    ForEach(aprovados) { estudante in
                        HStack {
                            Text(estudante.nome)
                            Spacer()
                            Text("Nota: \(String(format: "%.1f", estudante.nota))")
                        }
                    }
                }
            }
            .navigationTitle("Laços")
            .toolbar {
                Button("Adicionar") {
                    estudantes.append(
                        Estudante(nome: "Amanda", nota: 7.5)
                    )
                }
            }
        }
    }
}
```

Nesse exemplo:

- `estudantes` é um array de structs;
- `ForEach` exibe todos os estudantes;
- `filter` separa apenas os aprovados;
- `sorted` ordena os aprovados pelo nome;
- o botão adiciona uma nova estudante à lista;
- a interface atualiza automaticamente por causa do `@State`.

---

## 30. Resumo dos laços

| Estrutura | Uso |
|---|---|
| `for` | Percorre arrays, intervalos e coleções |
| `ForEach` | Repete componentes visuais no SwiftUI |
| `while` | Repete enquanto uma condição for verdadeira |
| `repeat while` | Executa pelo menos uma vez e depois verifica a condição |
| `break` | Interrompe o laço |
| `continue` | Pula uma repetição |

---

## Pontos-chave

- Laços de repetição executam um código várias vezes.
- `for` é usado para percorrer coleções e intervalos.
- `ForEach` é o laço mais usado para criar elementos visuais no SwiftUI.
- `while` repete enquanto uma condição for verdadeira.
- `repeat while` executa o bloco pelo menos uma vez.
- `break` encerra um laço antes do fim.
- `continue` pula uma repetição.
- Arrays combinam muito bem com `ForEach` e `List`.
- Para listas visuais, prefira `ForEach` em vez de `while`.
- Métodos como `map`, `filter` e `sorted` ajudam a transformar, filtrar e ordenar coleções.

---

## Desafio

Crie uma tela em SwiftUI com:

- uma struct chamada `Produto`;
- os campos `nome`, `preco` e `categoria`;
- um array de produtos;
- uma `List` para exibir todos os produtos;
- uma seção mostrando apenas produtos com preço maior que `100`;
- um botão para adicionar um novo produto;
- suporte para remover produtos da lista.

Exemplo esperado:

```txt
Produtos

Mouse
Categoria: Eletrônicos
Preço: R$ 80.00

Teclado
Categoria: Eletrônicos
Preço: R$ 150.00

Produtos acima de R$ 100

Teclado
Preço: R$ 150.00
```