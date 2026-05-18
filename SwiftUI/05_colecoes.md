# Coleções em SwiftUI

Em programação, **coleções** são estruturas usadas para armazenar vários valores em uma única variável ou constante.

No Swift, as principais coleções são:

| Coleção | Uso |
|---|---|
| `Array` | Lista ordenada de valores |
| `Set` | Conjunto de valores únicos |
| `Dictionary` | Pares de chave e valor |

No SwiftUI, coleções são muito usadas para exibir listas, menus, cards, dados de formulários e conteúdos repetidos na interface.

---

## 1. O que são coleções?

Coleções permitem guardar vários dados juntos.

Exemplo sem coleção:

```swift
let aluno1 = "Marina"
let aluno2 = "João"
let aluno3 = "Bianca"
```

Exemplo com coleção:

```swift
let alunos = ["Marina", "João", "Bianca"]
```

Nesse caso, todos os nomes estão dentro de uma única lista chamada `alunos`.

---

## 2. Array

O `Array` é uma coleção ordenada de valores.

Isso significa que os elementos ficam em uma ordem específica e podem ser acessados por posição.

```swift
let nomes = ["Marina", "João", "Bianca"]
```

Também podemos declarar o tipo manualmente:

```swift
let nomes: [String] = ["Marina", "João", "Bianca"]
```

---

## 3. Acessando itens de um Array

Cada item de um array possui um índice.

O primeiro item fica na posição `0`.

```swift
let nomes = ["Marina", "João", "Bianca"]

print(nomes[0])
print(nomes[1])
print(nomes[2])
```

Resultado:

```txt
Marina
João
Bianca
```

---

## 4. Quantidade de itens

Para descobrir quantos itens existem em um array, usamos `.count`.

```swift
let nomes = ["Marina", "João", "Bianca"]

print(nomes.count)
```

Resultado:

```txt
3
```

---

## 5. Verificando se um Array está vazio

Usamos `.isEmpty` para verificar se um array está vazio.

```swift
let nomes: [String] = []

print(nomes.isEmpty)
```

Resultado:

```txt
true
```

---

## 6. Adicionando itens em um Array

Quando o array é criado com `var`, podemos adicionar novos itens.

```swift
var cursos = ["Design", "Programação"]

cursos.append("Inovação")

print(cursos)
```

Resultado:

```txt
["Design", "Programação", "Inovação"]
```

---

## 7. Removendo itens de um Array

Podemos remover um item usando o índice.

```swift
var cursos = ["Design", "Programação", "Inovação"]

cursos.remove(at: 1)

print(cursos)
```

Resultado:

```txt
["Design", "Inovação"]
```

Nesse exemplo, o item `"Programação"` foi removido porque estava na posição `1`.

---

## 8. Percorrendo um Array

Podemos percorrer os itens de um array com `for`.

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

## 9. Array em SwiftUI com ForEach

No SwiftUI, usamos `ForEach` para exibir itens de um array na tela.

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

---

## 10. Array em SwiftUI com List

O componente `List` é usado para criar listas visuais.

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

Nesse exemplo, cada curso aparece como um item da lista.

---

## 11. Array com números

Arrays também podem guardar números.

```swift
let notas = [8.5, 9.0, 7.5]
```

Exemplo calculando média:

```swift
let notas = [8.5, 9.0, 7.5]

let soma = notas.reduce(0, +)
let media = soma / Double(notas.count)

print(media)
```

Resultado:

```txt
8.333333333333334
```

---

## 12. Array com Struct

Em Swift, é muito comum criar arrays com `struct`.

Isso ajuda a organizar dados mais completos.

```swift
struct Estudante {
    let nome: String
    let curso: String
}
```

Criando uma lista de estudantes:

```swift
let estudantes = [
    Estudante(nome: "Marina", curso: "Design"),
    Estudante(nome: "João", curso: "Programação"),
    Estudante(nome: "Bianca", curso: "Inovação")
]
```

---

## 13. Array com Struct em SwiftUI

Para usar uma lista de structs no SwiftUI, é recomendado que a struct tenha um identificador único.

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
        List(estudantes) { estudante in
            VStack(alignment: .leading) {
                Text(estudante.nome)
                    .font(.headline)
                
                Text(estudante.curso)
                    .font(.subheadline)
            }
        }
    }
}
```

Nesse exemplo:

- `Estudante` é uma struct;
- `Identifiable` permite que o SwiftUI identifique cada item;
- `UUID()` cria um identificador único;
- `List` exibe os estudantes na tela.

---

## 14. Set

O `Set` é uma coleção que armazena valores únicos.

Diferente do `Array`, o `Set` não mantém uma ordem fixa e não permite valores repetidos.

```swift
let numeros: Set<Int> = [1, 2, 3, 3, 4]

print(numeros)
```

Resultado possível:

```txt
[2, 1, 4, 3]
```

O número `3` aparece apenas uma vez, mesmo tendo sido escrito duas vezes.

---

## 15. Quando usar Set?

Use `Set` quando você precisa garantir que os valores não se repitam.

Exemplo:

```swift
var linguagens: Set<String> = ["Swift", "JavaScript", "Python"]

linguagens.insert("Swift")
linguagens.insert("Java")

print(linguagens)
```

Resultado possível:

```txt
["Python", "Swift", "JavaScript", "Java"]
```

O valor `"Swift"` não é duplicado.

---

## 16. Verificando se um Set contém um valor

```swift
let linguagens: Set<String> = ["Swift", "JavaScript", "Python"]

print(linguagens.contains("Swift"))
```

Resultado:

```txt
true
```

---

## 17. Set em SwiftUI

Como o `Set` não possui ordem fixa, é comum transformá-lo em array para exibir na tela.

```swift
import SwiftUI

struct ContentView: View {
    let linguagens: Set<String> = ["Swift", "JavaScript", "Python"]
    
    var body: some View {
        VStack {
            ForEach(Array(linguagens), id: \.self) { linguagem in
                Text(linguagem)
            }
        }
    }
}
```

Se quiser ordenar os itens:

```swift
ForEach(Array(linguagens).sorted(), id: \.self) { linguagem in
    Text(linguagem)
}
```

---

## 18. Dictionary

O `Dictionary` é uma coleção que armazena valores no formato **chave e valor**.

```swift
let estudante = [
    "nome": "Carlos",
    "curso": "Programação"
]
```

Nesse exemplo:

| Chave | Valor |
|---|---|
| `"nome"` | `"Carlos"` |
| `"curso"` | `"Programação"` |

---

## 19. Acessando valores de um Dictionary

Para acessar um valor, usamos a chave.

```swift
let estudante = [
    "nome": "Carlos",
    "curso": "Programação"
]

print(estudante["nome"] ?? "Nome não encontrado")
```

Resultado:

```txt
Carlos
```

O operador `??` define um valor padrão caso a chave não exista.

---

## 20. Adicionando valores em um Dictionary

```swift
var estudante = [
    "nome": "Carlos",
    "curso": "Programação"
]

estudante["turno"] = "Manhã"

print(estudante)
```

Resultado possível:

```txt
["nome": "Carlos", "curso": "Programação", "turno": "Manhã"]
```

---

## 21. Alterando valores em um Dictionary

```swift
var estudante = [
    "nome": "Carlos",
    "curso": "Programação"
]

estudante["curso"] = "Design"

print(estudante["curso"] ?? "Curso não encontrado")
```

Resultado:

```txt
Design
```

---

## 22. Removendo valores de um Dictionary

```swift
var estudante = [
    "nome": "Carlos",
    "curso": "Programação",
    "turno": "Manhã"
]

estudante.removeValue(forKey: "turno")

print(estudante)
```

Resultado possível:

```txt
["nome": "Carlos", "curso": "Programação"]
```

---

## 23. Dictionary em SwiftUI

Podemos exibir valores de um dicionário na tela.

```swift
import SwiftUI

struct ContentView: View {
    let estudante = [
        "nome": "Carlos",
        "curso": "Programação",
        "turno": "Manhã"
    ]
    
    var body: some View {
        VStack(alignment: .leading, spacing: 8) {
            Text("Nome: \(estudante["nome"] ?? "Não informado")")
            Text("Curso: \(estudante["curso"] ?? "Não informado")")
            Text("Turno: \(estudante["turno"] ?? "Não informado")")
        }
        .padding()
    }
}
```

Resultado:

```txt
Nome: Carlos
Curso: Programação
Turno: Manhã
```

---

## 24. Percorrendo um Dictionary

Também podemos percorrer as chaves e valores de um dicionário.

```swift
let estudante = [
    "nome": "Carlos",
    "curso": "Programação"
]

for (chave, valor) in estudante {
    print("\(chave): \(valor)")
}
```

Resultado possível:

```txt
nome: Carlos
curso: Programação
```

---

## 25. Dictionary em SwiftUI com ForEach

Como o `Dictionary` não possui uma ordem fixa, é comum ordenar as chaves antes de exibir.

```swift
import SwiftUI

struct ContentView: View {
    let estudante = [
        "nome": "Carlos",
        "curso": "Programação",
        "turno": "Manhã"
    ]
    
    var body: some View {
        VStack(alignment: .leading, spacing: 8) {
            ForEach(estudante.keys.sorted(), id: \.self) { chave in
                Text("\(chave): \(estudante[chave] ?? "")")
            }
        }
        .padding()
    }
}
```

Resultado:

```txt
curso: Programação
nome: Carlos
turno: Manhã
```

---

## 26. Coleções mutáveis e imutáveis

Quando uma coleção é criada com `let`, ela não pode ser alterada.

```swift
let nomes = ["Marina", "João"]

// nomes.append("Bianca") // Erro
```

Quando é criada com `var`, ela pode ser alterada.

```swift
var nomes = ["Marina", "João"]

nomes.append("Bianca")

print(nomes)
```

Resultado:

```txt
["Marina", "João", "Bianca"]
```

---

## 27. Coleções com @State

No SwiftUI, podemos usar `@State` para alterar uma coleção e atualizar a interface.

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
- a `List` atualiza automaticamente.

---

## 28. Removendo itens com @State

```swift
import SwiftUI

struct ContentView: View {
    @State private var nomes = ["Marina", "João", "Bianca"]
    
    var body: some View {
        VStack {
            List {
                ForEach(nomes, id: \.self) { nome in
                    Text(nome)
                }
                .onDelete { indexSet in
                    nomes.remove(atOffsets: indexSet)
                }
            }
        }
    }
}
```

Nesse exemplo, o usuário pode arrastar um item para o lado e remover da lista.

---

## 29. Exemplo completo

```swift
import SwiftUI

struct Estudante: Identifiable {
    let id = UUID()
    let nome: String
    let curso: String
    let turno: String
}

struct ContentView: View {
    @State private var estudantes = [
        Estudante(nome: "Marina", curso: "Design", turno: "Manhã"),
        Estudante(nome: "João", curso: "Programação", turno: "Tarde"),
        Estudante(nome: "Bianca", curso: "Inovação", turno: "Manhã")
    ]
    
    var body: some View {
        NavigationStack {
            List {
                ForEach(estudantes) { estudante in
                    VStack(alignment: .leading, spacing: 6) {
                        Text(estudante.nome)
                            .font(.headline)
                        
                        Text("Curso: \(estudante.curso)")
                            .font(.subheadline)
                        
                        Text("Turno: \(estudante.turno)")
                            .font(.caption)
                    }
                }
                .onDelete { indexSet in
                    estudantes.remove(atOffsets: indexSet)
                }
            }
            .navigationTitle("Estudantes")
            .toolbar {
                Button("Adicionar") {
                    estudantes.append(
                        Estudante(
                            nome: "Carlos",
                            curso: "Programação",
                            turno: "Tarde"
                        )
                    )
                }
            }
        }
    }
}
```

Nesse exemplo:

- `estudantes` é um array de structs;
- cada estudante possui `nome`, `curso` e `turno`;
- a tela exibe uma lista;
- o botão adiciona um novo estudante;
- o usuário pode remover itens da lista.

---

## 30. Resumo das coleções

| Coleção | Característica | Exemplo |
|---|---|---|
| `Array` | Lista ordenada | `["Marina", "João"]` |
| `Set` | Valores únicos, sem ordem fixa | `["Swift", "Python"]` |
| `Dictionary` | Chave e valor | `["nome": "Carlos"]` |

---

## Pontos-chave

- Coleções armazenam vários valores.
- `Array` é uma lista ordenada.
- `Set` armazena valores únicos.
- `Dictionary` armazena dados em chave e valor.
- Arrays são muito usados com `List` e `ForEach`.
- Sets não permitem valores repetidos.
- Dicionários são úteis para dados simples com chave e valor.
- Coleções criadas com `let` são imutáveis.
- Coleções criadas com `var` são mutáveis.
- Em SwiftUI, coleções com `@State` atualizam a interface quando mudam.
- Para listas de objetos, é comum usar `struct` com `Identifiable`.

---

## Desafio

Crie uma tela em SwiftUI com:

- uma struct chamada `Produto`;
- os campos `nome`, `categoria` e `preco`;
- um array de produtos;
- uma `List` exibindo os produtos;
- um botão para adicionar um novo produto;
- suporte para remover produtos da lista.

Exemplo esperado:

```txt
Produtos

Notebook
Categoria: Eletrônicos
Preço: R$ 3500.00

Caderno
Categoria: Papelaria
Preço: R$ 25.00
```