# 📘 Sistema Bancário em Java — Comentado Linha por Linha

# Classe Conta

```java
// Classe abstrata chamada Conta
// Ela serve como modelo para outras classes
abstract class Conta {

    // Atributo privado que guarda o número da conta
    private String numero;

    // Atributo privado que guarda o nome do cliente
    private String nome;

    // Atributo privado que guarda o saldo da conta
    private double saldo;

    // Primeiro construtor
    // Recebe número e nome
    public Conta(String numero, String nome)
    {
        // this.numero representa o atributo da classe
        // numero representa o parâmetro recebido
        this.numero = numero;

        // Inicializa o nome
        this.nome = nome;

        // Toda conta criada começa com saldo 0
        this.saldo = 0;
    }

    // Segundo construtor (sobrecarga)
    // Permite criar conta já com saldo inicial
    public Conta(String numero, String nome, double saldo)
    {
        // Inicializa número
        this.numero = numero;

        // Inicializa nome
        this.nome = nome;

        // Inicializa saldo
        this.saldo = saldo;
    }

    // Método setter do número
    // Serve para alterar o número da conta
    public void setNumero(String numero)
    {
        this.numero = numero;
    }

    // Método getter do número
    // Serve para retornar o número da conta
    public String getNumero()
    {
        return(this.numero);
    }

    // Método setter do nome
    public void setNome(String nome)
    {
        this.nome = nome;
    }

    // Método getter do nome
    public String getNome()
    {
        return(this.nome);
    }

    // Método getter do saldo
    // Não existe setSaldo para evitar alterações indevidas
    public double getSaldo()
    {
        return(this.saldo);
    }

    // Método que mostra os dados da conta
    public void mostrarDados()
    {
        // Exibe número da conta
        System.out.println(
            "\nConta = " + this.numero +

            // Exibe nome
            "\nNome = " + this.nome +

            // Exibe saldo
            "\nSaldo = " + this.saldo
        );
    }

    // Método que adiciona dinheiro na conta
    public void creditar(double valor)
    {
        // Soma o valor ao saldo atual
        this.saldo = this.saldo + valor;
    }

    // Método que retira dinheiro da conta
    public void debitar(double valor)
    {
        // Subtrai o valor do saldo
        this.saldo = this.saldo - valor;
    }

    // Método de transferência
    // Recebe:
    // - conta destino
    // - valor da transferência
    public void transferirPara(Conta conta, double valor)
    {
        // Debita da conta atual
        this.debitar(valor);

        // Credita na conta destino
        conta.creditar(valor);
    }
}
```

---

# Classe ContaCorrente

```java
// Classe ContaCorrente herdando da classe Conta
class ContaCorrente extends Conta {

    // Constante CPMF
    // final significa que o valor não pode mudar
    final double CPMF = 0.0038;

    // Primeiro construtor
    public ContaCorrente(String numero, String nome)
    {
        // super chama o construtor da classe pai
        super(numero, nome);
    }

    // Segundo construtor
    public ContaCorrente(String numero, String nome, double saldo)
    {
        // Chama construtor da superclasse
        super(numero, nome, saldo);
    }

    // Override do método debitar
    // Sobrescreve o método da classe Conta
    public void debitar(double valor)
    {
        // Debita o valor acrescido do CPMF
        super.debitar(valor * (1 + CPMF));
    }

    // Método para mostrar dados da conta corrente
    public void mostrarDados()
    {
        // Mostra o tipo da conta
        System.out.println("\n Conta Corrente");

        // Chama o método da classe pai
        super.mostrarDados();
    }
}
```

---

# Classe ContaPoupanca

```java
// Classe ContaPoupanca herdando da classe Conta
class ContaPoupanca extends Conta {

    // Primeiro construtor
    public ContaPoupanca(String numero, String nome)
    {
        // Chama construtor da superclasse
        super(numero, nome);
    }

    // Segundo construtor
    public ContaPoupanca(String numero, String nome, double saldo)
    {
        // Chama construtor da superclasse
        super(numero, nome, saldo);
    }

    // Método exclusivo da poupança
    // Calcula juros sobre o saldo
    public void renderJuros(float juros)
    {
        // Calcula os juros e credita na conta
        super.creditar(
            super.getSaldo() * (juros / (float)100)
        );
    }

    // Método mostrarDados sobrescrito
    public void mostrarDados()
    {
        // Mostra o tipo da conta
        System.out.println("\n Poupanca");

        // Chama método da superclasse
        super.mostrarDados();
    }
}
```

---

# Classe Movimento

```java
// Classe principal do sistema
class Movimento {

    // Método principal
    // O programa começa aqui
    public static void main(String[] args) throws Exception
    {
        // Cria objeto ContaCorrente
        ContaCorrente cc = new ContaCorrente("1", "Joao");

        // Cria objeto ContaPoupanca
        ContaPoupanca cp = new ContaPoupanca("2", "Maria");

        // Mostra título
        System.out.println("Movimento Bancario");

        // Mostra texto dos créditos iniciais
        System.out.println("Creditos iniciais 1000 e 600");

        // Deposita 1000 na conta corrente
        cc.creditar(1000);

        // Mostra dados da conta corrente
        cc.mostrarDados();

        // Deposita 600 na poupança
        cp.creditar(600);

        // Mostra dados da poupança
        cp.mostrarDados();

        // Pausa o sistema
        JUtil.pause();

        // Mostra mensagem de débito
        System.out.println("Debitando 100 e 50");

        // Debita 100 da conta corrente
        // Será acrescentado CPMF
        cc.debitar(100);

        // Mostra dados da corrente
        cc.mostrarDados();

        // Debita 50 da poupança
        cp.debitar(50);

        // Mostra dados da poupança
        cp.mostrarDados();

        // Pausa
        JUtil.pause();

        // Mostra mensagem de transferência
        System.out.println(
            "Transferindo 100 da Conta Corrente para Poupanca"
        );

        // Transfere 100 da corrente para poupança
        cc.transferirPara(cp, 100);

        // Mostra conta corrente
        cc.mostrarDados();

        // Mostra poupança
        cp.mostrarDados();

        // Pausa
        JUtil.pause();

        // Mostra mensagem de juros
        System.out.println("Rendendo juros da poupanca");

        // Aplica 10% de juros
        cp.renderJuros(10);

        // Mostra dados atualizados
        cp.mostrarDados();

        // Última pausa
        JUtil.pause();
    }
}
```

---

# 📘 Conceitos de POO Usados no Código

| Conceito | Exemplo no código |
|---|---|
| Classe | Conta, ContaCorrente |
| Objeto | cc e cp |
| Encapsulamento | atributos private |
| Herança | extends Conta |
| Polimorfismo | override do método debitar |
| Classe Abstrata | abstract class Conta |
| Construtores | Conta(), ContaCorrente() |
| Métodos | creditar(), debitar() |
| Sobrecarga | dois construtores |
| Reutilização | uso de super |

---

# 📘 Resumo Final

Este sistema bancário é um ótimo exemplo de Programação Orientada a Objetos.

Ele demonstra:

- reutilização de código com herança;
- proteção de dados com encapsulamento;
- personalização de métodos com polimorfismo;
- organização usando classes e objetos.

A classe Conta funciona como uma base para todas as contas.
As subclasses especializam os comportamentos:

- ContaCorrente aplica CPMF;
- ContaPoupanca aplica juros.

O programa Movimento simula operações reais de um banco:

- depósitos;
- saques;
- transferências;
- rendimento de juros.