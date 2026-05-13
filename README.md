# 📘 Resumo Completo de POO (Programação Orientada a Objetos)

A **Programação Orientada a Objetos (POO)** é uma forma de programar baseada em objetos do mundo real, como pessoas, carros, celulares, animais e contas bancárias.

A ideia principal é organizar o código de forma mais simples, reutilizável e fácil de manter.

---

# I. Abstração

A **abstração** consiste em mostrar apenas o que é importante de um objeto e esconder os detalhes complicados.

## Exemplos do mundo real

- Você dirige um carro usando volante, freio e acelerador, sem precisar entender o motor.
- Você usa um celular sem conhecer o código interno dele.

👉 Na programação fazemos isso usando **classes**, que representam apenas as características essenciais dos objetos.

---

# II. Classes

As **classes** são os moldes dos objetos.

Elas agrupam:
- atributos → características
- métodos → ações

---

## Exemplo: Classe Pessoa

Uma pessoa possui características e comportamentos.

### Atributos (dados)

- nome
- cor
- altura
- peso
- sexo

### Métodos (ações)

- falar()
- andar()
- comer()

---

## Exemplo em Java

```java
class Pessoa {
    String nome;
    String cor;
    float altura;
    float peso;
    char sexo;
}
```

---

# III. Métodos

Os **métodos** representam as ações que o objeto pode executar.

## Exemplo

Uma pessoa pode:
- comer
- andar
- correr
- falar
- pensar
- sorrir

---

## Exemplo em Java

```java
public class Pessoa {

    String nome, cor;
    float altura, peso;
    char sexo;

    public void comer() {}

    public void andar() {}

    public void correr() {}

    public void falar() {}

    public void pensar() {}

    public void sorrir() {}

    public void reagir() {}
}
```

---

# IV. Instância (Objeto)

Uma **instância** é um objeto criado a partir de uma classe.

## Conceito

- Classe = molde
- Objeto = elemento real criado a partir do molde

## Exemplo

Classe:
```java
Pessoa
```

Objetos:
- Pedro
- Marta
- Jony

## Criando um objeto

```java
Pessoa pessoa1;
pessoa1 = new Pessoa();
```

## Usando o objeto

```java
pessoa1.nome = "Pedro";
pessoa1.altura = 1.95f;
pessoa1.peso = 95f;
pessoa1.sexo = 'M';

pessoa1.andar();
pessoa1.correr();
pessoa1.reagir();
```

---

# V. Construtores

Os **construtores** são métodos especiais executados automaticamente quando o objeto é criado.

Eles servem para inicializar os atributos.

## Características

- têm o mesmo nome da classe;
- não possuem `return`;
- executam automaticamente.

## Exemplo

```java
class Circulo {

    float raio;

    public Circulo(float raio) {
        this.raio = raio;
    }
}
```

Criando o objeto:

```java
Circulo c = new Circulo(10);
```

---

# VI. Encapsulamento

O **encapsulamento** protege os dados do objeto.

Usamos `private` para impedir acesso direto aos atributos.

## Exemplo

```java
private float raio;
```

Métodos de acesso:

```java
public void setRaio(float raio) {
    this.raio = raio;
}

public float getRaio() {
    return this.raio;
}
```

---

# VII. Herança

A **herança** permite criar classes novas reaproveitando características de outra classe.

## Exemplo

```java
class Retangulo {
    float ladoA;
    float ladoB;
}
```

```java
class Paralelepipedo extends Retangulo {
    float altura;
}
```

---

# VIII. Polimorfismo

Polimorfismo significa:
> “muitas formas”.

O mesmo método pode funcionar de maneiras diferentes dependendo do objeto.

## Exemplo

```java
double area()
```

Cada classe implementa de sua forma.

---

# IX. Sobrecarga (Overloading)

A sobrecarga acontece quando criamos métodos com o mesmo nome, mas parâmetros diferentes.

## Exemplo

```java
public int quadrado(int x) {
    return x * x;
}
```

```java
public double quadrado(double x) {
    return x * x;
}
```

---

# X. Classe Círculo (Exemplo Completo)

## Fórmulas

Diâmetro:

d = 2r

Área:

A = πr²

Comprimento:

C = 2πr

## Código em Java

```java
class Circulo {

    float raio;
    float x, y;

    float diametro() {
        return this.raio * 2f;
    }

    double area() {
        return Math.PI * Math.pow(this.raio, 2);
    }

    double comprimento() {
        return 2 * Math.PI * this.raio;
    }
}
```

---

# XI. Vetores em POO

Vetores podem armazenar objetos.

## Exemplo

```java
Classe[] v = new Classe[3];

v[0] = new Classe();
```

---

# XII. Classes Abstratas

Classes abstratas servem apenas como modelo.

## Exemplo

```java
abstract class FiguraPlana {

    abstract double area();

    abstract double perimetro();
}
```

---

# XIII. Resumo Geral

| Conceito | Função |
|---|---|
| Abstração | Mostrar apenas o essencial |
| Classe | Molde do objeto |
| Objeto/Instância | Elemento criado da classe |
| Atributos | Características |
| Métodos | Ações |
| Construtor | Inicializa o objeto |
| Encapsulamento | Protege os dados |
| Herança | Reaproveita código |
| Polimorfismo | Mesmo método, várias formas |
| Sobrecarga | Mesmo método com parâmetros diferentes |
| Classe Abstrata | Modelo para subclasses |

---

# XIV. Conclusão

A Programação Orientada a Objetos ajuda a criar sistemas:
- organizados;
- reutilizáveis;
- seguros;
- fáceis de manter.

Ela é uma das bases mais importantes da programação moderna.