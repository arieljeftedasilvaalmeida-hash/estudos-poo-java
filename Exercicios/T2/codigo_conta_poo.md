# 📘 Análise Completa do Código Bancário em Java (POO)

# Introdução

Este código foi desenvolvido utilizando os principais conceitos da Programação Orientada a Objetos (POO):

- Classes
- Objetos
- Encapsulamento
- Herança
- Polimorfismo
- Classes Abstratas
- Construtores
- Métodos

O sistema simula movimentações bancárias entre contas.

---

# 🔷 Classe Abstrata Conta

```java
abstract class Conta {
```

- `abstract` significa que esta classe é abstrata.
- Serve como modelo para outras classes.
- Não pode ser instanciada diretamente.

---

```java
private String numero;
private String nome;
private double saldo;
```

- Atributos privados.
- O encapsulamento protege os dados.

Atributos:
- numero → número da conta
- nome → nome do cliente
- saldo → dinheiro disponível

---

# 🔷 Construtores

```java
public Conta(String numero, String nome)
```

- Construtor da classe.
- Executado automaticamente ao criar o objeto.

---

```java
this.numero = numero;
this.nome = nome;
this.saldo = 0;
```

- `this` representa o próprio objeto.
- Inicializa os atributos.

---

```java
public Conta(String numero, String nome, double saldo)
```

- Sobrecarga de construtor.
- Permite criar conta com saldo inicial.

---

# 🔷 Getters e Setters

```java
public void setNumero(String numero)
```

- Método setter.
- Altera o número da conta.

---

```java
public String getNumero()
```

- Método getter.
- Retorna o número da conta.

---

# 🔷 Método mostrarDados

```java
public void mostrarDados()
```

- Exibe os dados da conta.

```java
System.out.println()
```

Mostra:
- número
- nome
- saldo

---

# 🔷 Método creditar

```java
public void creditar(double valor)
```

- Deposita dinheiro na conta.

```java
this.saldo = this.saldo + valor;
```

- Soma valor ao saldo.

---

# 🔷 Método debitar

```java
public void debitar(double valor)
```

- Retira dinheiro da conta.

```java
this.saldo = this.saldo - valor;
```

- Subtrai o valor do saldo.

---

# 🔷 Método transferirPara

```java
public void transferirPara(Conta conta, double valor)
```

- Faz transferência entre contas.

```java
this.debitar(valor);
```

- Retira da conta atual.

```java
conta.creditar(valor);
```

- Adiciona na conta destino.

---

# 🔷 Classe ContaCorrente

```java
class ContaCorrente extends Conta
```

- Herda da classe Conta.

---

# 🔷 Constante CPMF

```java
final double CPMF = 0.0038;
```

- Constante que representa a taxa CPMF.

---

# 🔷 Método debitar com Override

```java
public void debitar(double valor)
```

- Sobrescreve o método da superclasse.

```java
super.debitar(valor * (1 + CPMF));
```

- Aplica CPMF ao débito.

Exemplo:
- saque = 100
- valor debitado = 100.38

---

# 🔷 Classe ContaPoupanca

```java
class ContaPoupanca extends Conta
```

- Herda da classe Conta.

---

# 🔷 Método renderJuros

```java
public void renderJuros(float juros)
```

- Calcula rendimento da poupança.

```java
super.creditar(super.getSaldo() * (juros/(float)100));
```

- Calcula os juros e credita na conta.

---

# 🔷 Classe Movimento

```java
class Movimento
```

- Classe principal do programa.

---

# 🔷 Método main

```java
public static void main(String[] args)
```

- Início da execução do sistema.

---

# 🔷 Criando Objetos

```java
ContaCorrente cc = new ContaCorrente("1","Joao");
```

- Cria uma conta corrente.

```java
ContaPoupanca cp = new ContaPoupanca("2","Maria");
```

- Cria uma conta poupança.

---

# 🔷 Créditos iniciais

```java
cc.creditar(1000);
```

- Deposita 1000 na conta corrente.

```java
cp.creditar(600);
```

- Deposita 600 na poupança.

---

# 🔷 Débitos

```java
cc.debitar(100);
```

- Debita 100 + CPMF.

```java
cp.debitar(50);
```

- Debita 50 da poupança.

---

# 🔷 Transferência

```java
cc.transferirPara(cp,100);
```

- Transfere 100 da corrente para poupança.

---

# 🔷 Rendendo Juros

```java
cp.renderJuros(10);
```

- Aplica 10% de juros na poupança.

---

# 🔷 Pausas

```java
JUtil.pause();
```

- Pausa a execução do programa.

---

# 📘 Conceitos de POO Aplicados

| Conceito | Onde aparece |
|---|---|
| Classe | Conta, ContaCorrente |
| Objeto | cc e cp |
| Encapsulamento | atributos private |
| Herança | extends Conta |
| Polimorfismo | override debitar |
| Classe Abstrata | abstract class Conta |
| Construtor | Conta(), ContaCorrente() |
| Métodos | creditar(), debitar() |

---

# 📘 Resumo Final

Este sistema bancário demonstra como a Programação Orientada a Objetos organiza o código de forma:

- reutilizável;
- organizada;
- segura;
- fácil de manter.

A herança evita repetição de código.
O encapsulamento protege os dados.
O polimorfismo permite alterar comportamentos.
As classes abstratas criam modelos reutilizáveis.
