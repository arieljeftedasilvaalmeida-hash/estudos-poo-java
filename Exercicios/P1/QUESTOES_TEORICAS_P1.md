# Provas P1 — Programação Orientada a Objetos

---

## Prova 1 — P1 26/10/2022

### Q1 [1,0]
**Qual a diferença entre um recurso (método, por exemplo) estático e um recurso dinâmico?**

- **Estático (`static`)** → pertence à classe. Não precisa criar objeto para usar. Chamado pela classe: `Classe.metodo()`
- **Dinâmico** → pertence ao objeto. Só existe após criar um objeto com `new`. Chamado pelo objeto: `obj.metodo()`

---

### Q2 [1,0]
**Explique a sentença:** *"As variáveis de referência são criadas dentro da classe de definição (classe base) e, assim como os métodos, são acessadas por meio de objetos".*

**Falso.** As variáveis são *declaradas* na classe, mas *criadas* na instância (objeto) e acessadas por ele.

---

## Prova 2 — P1 09/10/2024

### Q1 [1,0]
**Afirmação:** *"Na programação orientada a objetos, a sobrecarga de métodos significa ter vários métodos com nomes iguais mas assinaturas diferentes. A assinatura de um método é dada pela junção do seu nome e seus parâmetros de entrada. A ordem na passagem de parâmetros não interfere na sobrecarga. Da mesma forma, o tipo de retorno não interfere na sobrecarga."* Informe verdadeiro ou falso e justifique.

**Falso.** A sentença erra ao afirmar que a ordem dos parâmetros não interfere na sobrecarga. Na verdade, ela interfere, pois métodos com os mesmos parâmetros em ordens diferentes são considerados assinaturas distintas:

```java
public void metodo(int a, String b) { }  // assinatura diferente de:
public void metodo(String b, int a) { }  // esta
```

---

### Q2 [1,0]
**Quais são as diferenças no uso de vetor em Java (POO) em relação a uma linguagem imperativa clássica?**

Em linguagens imperativas clássicas (como C), o vetor armazena dados primitivos diretamente. Em Java com POO, o vetor armazena **referências para objetos**, ou seja, cada posição aponta para uma instância de uma classe:

```java
// Imperativa — armazena valor direto
int[] numeros = new int[3];

// POO — armazena referência para objeto
Partido[] v = new Partido[3];
v[0] = new Partido(); // cada posição precisa ser instanciada
```

---

## Prova 3 — P1 17/04/2024

### Q1 [1,0]
**Afirmação:** *"Em programação orientada a objetos, chama-se instância de uma classe, um objeto cujo comportamento e estado são definidos pela classe. As instâncias de uma classe têm o mesmo conjunto de atributos, embora sejam diferentes quanto ao conteúdo desses atributos. Os métodos são definidos na classe e cada objeto recebe uma cópia destes."* Informe verdadeiro ou falso e justifique.

**Falso.** A sentença erra ao dizer que cada objeto recebe uma *cópia* dos métodos. Na verdade, os métodos são **compartilhados** por todos os objetos da classe. O que cada objeto possui de forma individual são apenas os **atributos** (estado).

---

### Q2 [1,0]
**Afirmação:** *"Sobrecarregar métodos significa ter vários atributos e métodos com nomes iguais mas assinaturas diferentes. O tipo de retorno não interfere na validação sintática da sobrecarga."* Informe verdadeiro ou falso e justifique.

**Falso (parcialmente).** A sentença erra ao afirmar que sobrecarga se aplica a **atributos**. Sobrecarga se aplica apenas a **métodos**. O restante está correto — o tipo de retorno realmente não interfere na sobrecarga.

---

## Prova 4 — P1 03/05/2023

### Q1 [1,0]
**Explique quais as vantagens em usar o recurso de sobrecarga de métodos na criação de classes.**

A sobrecarga permite que uma mesma operação seja realizada de formas diferentes, sem precisar criar nomes distintos para cada variação. Isso torna o código mais legível e intuitivo, pois o programador usa um mesmo nome de método independentemente dos tipos ou quantidade de parâmetros passados.

---

### Q2 [1,0]
**Afirmação:** *"Podemos criar objetos a partir de classes. Esse processo é chamado instância. Quando um objeto é criado é feita uma cópia de toda a sua estrutura (a classe), tanto atributos quanto métodos. O mesmo acontece com outros objetos criados a partir desta classe."* Informe verdadeiro ou falso e justifique.

**Falso.** A sentença erra ao dizer que é feita uma cópia de toda a estrutura, incluindo métodos. Na verdade, cada objeto recebe apenas uma cópia dos **atributos**. Os **métodos** são compartilhados entre todos os objetos da classe.

---

## Prova 5 — P1 22/04/2025

### Q1 [1,0]
**Afirmação:** *"A programação orientada a objeto permite que você crie métodos com o mesmo nome, desde que eles tenham parâmetros diferentes. Este recurso é chamado sobrecarga de métodos. A determinação do método a ser chamado vai depender da forma como o programador resolver passar os parâmetros. Então a checagem destes parâmetros é feita apenas no momento da execução do programa, não necessitando checagem no momento da compilação."* Informe verdadeiro ou falso e justifique.

**Falso.** A checagem da sobrecarga ocorre em **tempo de compilação**, não de execução. O compilador determina qual método invocar com base nos tipos e ordem dos argumentos passados.

---

### Q2 [1,0]
**Quais são as diferenças no uso de vetor em Java (POO) em relação a uma linguagem imperativa clássica?**

Em Java com POO, o vetor armazena **referências para objetos**, ou seja, cada posição aponta para uma instância de uma classe — diferente de linguagens imperativas clássicas, onde o vetor armazena valores primitivos diretamente na memória.

```java
// Imperativa — armazena valor direto
int[] numeros = new int[3];

// POO — armazena referência para objeto
Produto[] produtos = new Produto[3];
produtos[0] = new Produto(); // cada posição precisa ser instanciada
```
