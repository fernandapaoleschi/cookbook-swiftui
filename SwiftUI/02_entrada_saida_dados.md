# Entrada e Saída de Dados em SwiftUI

Em programação, **entrada de dados** é quando o usuário informa algum valor para o sistema.

Já a **saída de dados** é quando o sistema exibe alguma informação para o usuário.

No SwiftUI, a entrada e a saída de dados acontecem principalmente por meio dos componentes visuais da interface.

---

## 1. O que é saída de dados?

A saída de dados acontece quando mostramos uma informação na tela.

Em SwiftUI, o principal componente usado para exibir textos é o `Text`.

### Exemplo

```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        Text("Olá, mundo!")
    }
}
```

Nesse exemplo, a frase `"Olá, mundo!"` aparece na tela do aplicativo.

---

## 2. Exibindo variáveis na tela

Também podemos exibir valores armazenados em variáveis ou constantes.

```swift
import SwiftUI

struct ContentView: View {
    let nome = "Marina"
    
    var body: some View {
        Text("Olá, \(nome)!")
    }
}
```

Resultado exibido na tela:

```txt
Olá, Marina!
```

O trecho `\(nome)` é chamado de **interpolação de string**.

Ele permite colocar o valor de uma variável dentro de um texto.

---

## 3. Exibindo números

Podemos exibir valores numéricos usando interpolação.

```swift
import SwiftUI

struct ContentView: View {
    let idade = 21
    
    var body: some View {
        Text("Idade: \(idade)")
    }
}
```

Resultado:

```txt
Idade: 21
```

---

## 4. Personalizando a saída de dados

O componente `Text` pode receber modificadores para alterar a aparência do texto.

```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        Text("Cookbook SwiftUI")
            .font(.title)
            .bold()
            .foregroundStyle(.blue)
    }
}
```

Nesse exemplo:

- `.font(.title)` aumenta o tamanho do texto;
- `.bold()` deixa o texto em negrito;
- `.foregroundStyle(.blue)` altera a cor do texto.

---

## 5. O que é entrada de dados?

A entrada de dados acontece quando o usuário informa algum valor para o aplicativo.

Em SwiftUI, usamos componentes como:

| Componente | Uso |
|---|---|
| `TextField` | Entrada de texto |
| `SecureField` | Entrada de senha |
| `Toggle` | Entrada booleana |
| `Stepper` | Entrada numérica |
| `Slider` | Entrada numérica com controle deslizante |
| `Picker` | Escolha entre opções |

---

## 6. Entrada de texto com TextField

O `TextField` permite que o usuário digite um texto.

Para que o texto digitado seja armazenado, usamos uma variável com `@State`.

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

- `@State private var nome = ""` cria uma variável que pode mudar;
- `TextField` recebe o texto digitado pelo usuário;
- `$nome` cria uma ligação entre o campo e a variável;
- `Text` exibe o valor atualizado na tela.

---

## 7. Entendendo o @State

O `@State` é usado quando uma informação pode mudar dentro da tela.

```swift
@State private var nome = ""
```

Quando o valor de `nome` muda, o SwiftUI atualiza a interface automaticamente.

Por isso, quando digitamos no `TextField`, o texto exibido no `Text` muda ao mesmo tempo.

---

## 8. Entendendo o símbolo $

No SwiftUI, usamos `$` quando queremos criar uma conexão de mão dupla entre a interface e uma variável.

Exemplo:

```swift
TextField("Digite seu nome", text: $nome)
```

Isso significa que:

- se o usuário digitar algo, a variável `nome` muda;
- se a variável `nome` mudar, o campo também é atualizado.

Esse processo é chamado de **binding**.

---

## 9. Entrada de senha com SecureField

O `SecureField` é parecido com o `TextField`, mas esconde o conteúdo digitado.

Ele é usado para senhas.

```swift
import SwiftUI

struct ContentView: View {
    @State private var senha = ""
    
    var body: some View {
        VStack(spacing: 16) {
            SecureField("Digite sua senha", text: $senha)
                .textFieldStyle(.roundedBorder)
            
            Text("Senha digitada com \(senha.count) caracteres")
        }
        .padding()
    }
}
```

Nesse exemplo, a senha não aparece diretamente na tela.

---

## 10. Entrada booleana com Toggle

O `Toggle` é usado para valores do tipo `Bool`, ou seja, verdadeiro ou falso.

```swift
import SwiftUI

struct ContentView: View {
    @State private var receberNotificacoes = false
    
    var body: some View {
        VStack(spacing: 16) {
            Toggle("Receber notificações", isOn: $receberNotificacoes)
            
            Text(receberNotificacoes ? "Notificações ativadas" : "Notificações desativadas")
        }
        .padding()
    }
}
```

Nesse exemplo:

- quando o botão está ligado, o valor é `true`;
- quando está desligado, o valor é `false`.

---

## 11. Entrada numérica com Stepper

O `Stepper` permite aumentar ou diminuir um valor numérico.

```swift
import SwiftUI

struct ContentView: View {
    @State private var idade = 18
    
    var body: some View {
        VStack(spacing: 16) {
            Stepper("Idade: \(idade)", value: $idade, in: 0...100)
            
            Text("Sua idade é \(idade) anos")
        }
        .padding()
    }
}
```

Nesse exemplo:

- o valor inicial é `18`;
- o usuário pode aumentar ou diminuir a idade;
- o valor fica limitado entre `0` e `100`.

---

## 12. Entrada numérica com Slider

O `Slider` permite escolher um valor deslizando uma barra.

```swift
import SwiftUI

struct ContentView: View {
    @State private var volume = 50.0
    
    var body: some View {
        VStack(spacing: 16) {
            Slider(value: $volume, in: 0...100)
            
            Text("Volume: \(Int(volume))")
        }
        .padding()
    }
}
```

Nesse exemplo, o valor do volume varia de `0` até `100`.

Como o `Slider` trabalha com números decimais, usamos `Int(volume)` para mostrar o valor inteiro na tela.

---

## 13. Escolha de opções com Picker

O `Picker` permite que o usuário escolha uma opção entre várias.

```swift
import SwiftUI

struct ContentView: View {
    @State private var linguagemSelecionada = "Swift"
    
    let linguagens = ["Swift", "JavaScript", "Python", "Java"]
    
    var body: some View {
        VStack(spacing: 16) {
            Picker("Escolha uma linguagem", selection: $linguagemSelecionada) {
                ForEach(linguagens, id: \.self) { linguagem in
                    Text(linguagem)
                }
            }
            .pickerStyle(.menu)
            
            Text("Linguagem escolhida: \(linguagemSelecionada)")
        }
        .padding()
    }
}
```

Nesse exemplo:

- a variável `linguagemSelecionada` guarda a opção escolhida;
- o `ForEach` percorre a lista de linguagens;
- o `Text` exibe a escolha do usuário.

---

## 14. Entrada e saída juntas

Em SwiftUI, é muito comum receber um dado do usuário e exibir esse valor na tela ao mesmo tempo.

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    @State private var idade = 18
    
    var body: some View {
        VStack(spacing: 20) {
            Text("Cadastro")
                .font(.title)
                .bold()
            
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Stepper("Idade: \(idade)", value: $idade, in: 0...120)
            
            Text("Nome: \(nome)")
            Text("Idade: \(idade)")
        }
        .padding()
    }
}
```

Nesse exemplo, o usuário informa o nome e a idade, e os dados são exibidos logo abaixo.

---

## 15. Exibindo mensagem ao clicar em um botão

Também podemos usar um `Button` para controlar quando a saída de dados será exibida.

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    @State private var mensagem = ""
    
    var body: some View {
        VStack(spacing: 16) {
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Button("Enviar") {
                mensagem = "Olá, \(nome)!"
            }
            
            Text(mensagem)
        }
        .padding()
    }
}
```

Nesse exemplo:

- o usuário digita o nome;
- ao clicar no botão, a mensagem é criada;
- o texto aparece na tela.

---

## 16. Exemplo com dados preenchidos

Neste exemplo, alguns dados já começam preenchidos para facilitar a visualização da saída de dados.

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = "Bianca"
    @State private var idade = 19
    @State private var cursoSelecionado = "Design"
    @State private var receberNotificacoes = true
    
    let cursos = ["Design", "Programação", "Inovação"]
    
    var body: some View {
        VStack(spacing: 20) {
            Text("Perfil do Estudante")
                .font(.title2)
                .bold()
            
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Stepper("Idade: \(idade)", value: $idade, in: 0...120)
            
            Picker("Curso", selection: $cursoSelecionado) {
                ForEach(cursos, id: \.self) { curso in
                    Text(curso)
                }
            }
            .pickerStyle(.menu)
            
            Toggle("Receber notificações", isOn: $receberNotificacoes)
            
            Text("Nome: \(nome)")
            Text("Idade: \(idade)")
            Text("Curso: \(cursoSelecionado)")
            Text("Notificações: \(receberNotificacoes ? "Sim" : "Não")")
        }
        .padding()
    }
}
```

Resultado inicial esperado:

```txt
Nome: Bianca
Idade: 19
Curso: Design
Notificações: Sim
```

---

## 17. Exemplo completo

```swift
import SwiftUI

struct ContentView: View {
    @State private var nome = ""
    @State private var idade = 18
    @State private var receberNotificacoes = false
    @State private var cursoSelecionado = "Programação"
    @State private var mensagemFinal = ""
    
    let cursos = ["Design", "Programação", "Inovação"]
    
    var body: some View {
        VStack(spacing: 20) {
            Text("Entrada e Saída de Dados")
                .font(.title2)
                .bold()
            
            TextField("Digite seu nome", text: $nome)
                .textFieldStyle(.roundedBorder)
            
            Stepper("Idade: \(idade)", value: $idade, in: 0...120)
            
            Toggle("Receber notificações", isOn: $receberNotificacoes)
            
            Picker("Curso", selection: $cursoSelecionado) {
                ForEach(cursos, id: \.self) { curso in
                    Text(curso)
                }
            }
            .pickerStyle(.menu)
            
            Button("Exibir dados") {
                mensagemFinal = """
                Nome: \(nome)
                Idade: \(idade)
                Curso: \(cursoSelecionado)
                Notificações: \(receberNotificacoes ? "Sim" : "Não")
                """
            }
            
            Text(mensagemFinal)
                .multilineTextAlignment(.center)
        }
        .padding()
    }
}
```

---

## 18. Diferença entre entrada e saída

| Conceito | Significado | Exemplo em SwiftUI |
|---|---|---|
| Entrada de dados | Usuário informa algo | `TextField`, `Toggle`, `Picker` |
| Saída de dados | Sistema mostra algo | `Text`, imagens, mensagens |
| Estado | Valor que pode mudar na tela | `@State` |
| Binding | Ligação entre interface e variável | `$nome` |

---

## Pontos-chave

- Entrada de dados é quando o usuário informa valores.
- Saída de dados é quando o sistema exibe informações.
- Em SwiftUI, usamos `Text` para exibir informações.
- Usamos `TextField` para receber textos.
- Usamos `SecureField` para receber senhas.
- Usamos `Toggle` para valores `true` ou `false`.
- Usamos `Stepper` para aumentar ou diminuir números.
- Usamos `Slider` para escolher valores em uma faixa.
- Usamos `Picker` para escolher uma opção.
- O `@State` permite que uma variável mude e atualize a tela.
- O símbolo `$` cria uma ligação entre a variável e o componente visual.

---

## Desafio

Crie uma tela em SwiftUI com:

- um `TextField` para o usuário digitar o nome;
- um `Stepper` para escolher a idade;
- um `Picker` para escolher um curso;
- um `Toggle` para marcar se deseja receber notificações;
- um botão chamado `Confirmar`;
- um `Text` exibindo os dados preenchidos.

Exemplo esperado:

```txt
Nome: Carlos
Idade: 22
Curso: Programação
Notificações: Sim
```