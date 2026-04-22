# 📘 Estudos de POO (Programação Orientada a Objetos)

---

## I. Abstração

É o conceito de focar só no que é importante de um objeto, ignorando detalhes desnecessários para simplificar o sistema.

### Exemplos:
- **Carro:** você usa volante, freio e acelerador sem saber como o motor funciona por dentro.
- **Celular:** você usa apps e botões sem entender hardware ou código interno.

👉 Na programação, isso é feito com **classes**, que representam objetos do mundo real com apenas suas características essenciais.

---

## II. Classes

POO organiza tudo em **classes**, que reúnem dados e funções juntas.

### Exemplo:
- Em vez de funções separadas para uma pessoa, cria-se a classe `Pessoa`.

### Classe:
É um “molde” de um objeto.

### Exemplo:
- Classe `Pessoa` = modelo de pessoas.

---

### Atributos:
Características da classe (dados):

- nome  
- cor  
- altura  
- peso  
- sexo  

---

### Métodos:
Ações da classe:

- falar()  
- andar()  
- comer()  

---

### Exemplo em Java:
class Pessoa {
    String nome;
    String cor;
    float altura;
    float peso;
    char sexo;
}

---

## III. Métodos

São as ações que um objeto pode realizar (comportamentos).

### Exemplo:
Na classe Pessoa:

- comer  
- andar  
- correr  
- falar  
- pensar  
- sorrir  
- reagir  

---

### Em Java:
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

---

## IV. Instância

É quando você cria um objeto a partir de uma classe.

### Conceito:
- Classe = modelo
- Instância = objeto real

### Exemplo:
- Classe: Pessoa
- Instâncias: Pedro, Marta, Jony

---

### Processo:
Pessoa pessoa1;
pessoa1 = new Pessoa();

---

### Usando o objeto:
pessoa1.nome = "Pedro";
pessoa1.altura = 1.95f;
pessoa1.peso = 95f;
pessoa1.sexo = 'M';

pessoa1.andar();
pessoa1.correr();
pessoa1.reagir();

---

## V. POO – Exemplo Círculo

### Classe Círculo

- Atributo: raio

### Métodos:
- diametro() → 2 × raio  
- area() → π × raio²  
- comprimento() → 2 × π × raio  

---

### Exemplo em Java:
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

---

### Instanciando:
Circulo circulo1 = new Circulo();
circulo1.raio = 9f;

---

### Usando métodos:
System.out.println(circulo1.diametro());
System.out.println(circulo1.area());
System.out.println(circulo1.comprimento());

---

### Overloading (Sobrecarga):
public int quadrado(int x) {
    return x * x;
}

public double quadrado(double x) {
    return x * x;
}

---

## VI. Vetores em POO (Java)

- Armazenam **referências para objetos**, não os objetos diretamente  
- Precisam de **instanciação em cada posição** (`new`)  
- Tamanho definido na criação  
- Acesso por índice (`vetor[i]`)  

```java
Classe[] v = new Classe[3];
v[0] = new Classe();