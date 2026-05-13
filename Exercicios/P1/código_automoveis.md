# Análise de Código — Sistema de Cadastro e Avaliação de Automóveis

Este programa cadastra automóveis, calcula o consumo de combustível de cada um e exibe um relatório com classificação de eficiência, total de litros abastecidos e o veículo de melhor desempenho.

---

## Classe `Automoveis`

Representa a entidade "Automóvel" com seus atributos e comportamentos relacionados ao consumo de combustível.

```java
public class Automoveis {

    // Atributos de instância — cada objeto terá seus próprios valores
    int codigo;                // Código identificador do automóvel
    String descricao;          // Nome/descrição do automóvel
    double capacidadeTanque;   // Capacidade total do tanque em litros
    double litrosAbastecidos;  // Quantidade de litros abastecidos no teste
    double kmRodada;           // Quilometragem percorrida com os litros abastecidos

    // Método consumo() sem parâmetro — usa os litros abastecidos do próprio objeto
    // Retorna quantos km o automóvel percorre por litro (km/L)
    public double consumo() {
        return this.kmRodada / this.litrosAbastecidos; // km dividido por litros = consumo
    }

    // Método consumo(double) — sobrecarga: calcula consumo com um valor externo de litros
    // Útil para simular consumo com uma quantidade diferente da abastecida
    public double consumo(double litrosAbastecidos) {
        return this.kmRodada / litrosAbastecidos; // usa o parâmetro, não o atributo
    }

    // Método classificacao() — retorna uma string com a eficiência do automóvel
    // Baseada no consumo calculado pelo método consumo()
    public String classificacao() {
        String resultado;

        if (consumo() < 10)       resultado = "Ruim";   // Menos de 10 km/L
        else if (consumo() <= 13) resultado = "Normal"; // Entre 10 e 13 km/L
        else                      resultado = "Ótimo";  // Acima de 13 km/L

        return resultado;
    }

    // Método mostrarDados() — exibe todos os atributos e resultados calculados no console
    public void mostrarDados() {
        System.out.println(
            "Codigo: "               + this.codigo           +
            "\nDescricao: "          + this.descricao        +
            "\nCapacidade do tanque: "+ this.capacidadeTanque +
            "\nLitros abastecidos: " + this.litrosAbastecidos +
            "\nKm rodada: "          + this.kmRodada         +
            "\nConsumo: "            + this.consumo()        + // chama o método consumo()
            "\nClassificacao"        + this.classificacao()    // chama o método classificacao()
        );
    }
}
```

---

## Classe `LerAutomoveis`

Classe principal com o método `main`. Responsável pela leitura dos dados, processamento e exibição do relatório final.

```java
public class LerAutomoveis {

    public static void main(String[] args) throws Exception {

        // Variáveis de controle e acumulação
        double totalLitrosAbastecidos = 0; // Acumula o total de litros de todos os automóveis
        double melhorConsumo = 0;          // Guarda o maior consumo encontrado até o momento
        String melhorAutomovel = "";       // Guarda o nome do automóvel com melhor consumo
        int cont = 0;                      // Guarda o número (posição) do melhor automóvel

        // Solicita a quantidade de automóveis e cria o vetor de objetos
        System.out.print("Quantidade de automoveis: ");
        Automoveis a[] = new Automoveis[JUtil.readInt()]; // Cria vetor com tamanho informado

        // Loop de cadastro — percorre cada posição do vetor para ler os dados
        for (int i = 0; i < a.length; i++) {

            a[i] = new Automoveis(); // Instancia um novo objeto Automoveis na posição i

            // Lê e armazena os dados do automóvel
            System.out.print("Digite o Codigo: ");
            a[i].codigo = JUtil.readInt();

            System.out.print("\nDigite a descricao: ");
            a[i].descricao = JUtil.readString();

            System.out.print("\nDigite a capacidade de tanque: ");
            a[i].capacidadeTanque = JUtil.readDouble();

            System.out.print("\nQuantidade de litros abastecidos: ");
            a[i].litrosAbastecidos = JUtil.readDouble();

            System.out.print("\nDigite o KM rodado: ");
            a[i].kmRodada = JUtil.readDouble();

            totalLitrosAbastecidos += a[i].litrosAbastecidos; // Acumula os litros deste automóvel

            // Verifica se o consumo atual é melhor que o maior registrado até agora
            if (a[i].consumo() > melhorConsumo) {
                melhorConsumo    = a[i].consumo();   // Atualiza o maior consumo
                melhorAutomovel  = a[i].descricao;   // Atualiza o nome do melhor automóvel
                cont             = i + 1;            // Guarda a posição (começa em 1, não em 0)
            }
        }

        // Exibe o cabeçalho da tabela de resultados
        System.out.print("\nItem | Codigo | Descricao | ListroAb | KilometagemR | Consumo | Classificacao");

        // Loop de exibição — imprime uma linha da tabela para cada automóvel
        for (int i = 0; i < a.length; i++) {
            System.out.println(
                "\n   " + (i + 1)            + // Número do item na lista (baseado em 1)
                " | "  + a[i].codigo         + // Código do automóvel
                " | "  + a[i].descricao      + // Descrição/nome
                " | "  + a[i].litrosAbastecidos + // Litros abastecidos
                " | "  + a[i].kmRodada       + // Quilometragem rodada
                " | "  + a[i].consumo()      + // Consumo calculado (km/L)
                " | "  + a[i].classificacao()  // Classificação (Ruim / Normal / Ótimo)
            );
        }

        // Exibe os resultados consolidados finais
        System.out.print("\nTotal de litros abastecidos: " + totalLitrosAbastecidos);
        System.out.print("\nO melhor consumo foi " + melhorConsumo +
                         " do automovel " + cont + " - " + melhorAutomovel);
        // Exibe o consumo máximo encontrado e identifica o automóvel pelo número e nome
    }
}
```

---

## Resumo dos Conceitos Aplicados

| Conceito | Onde aparece |
|---|---|
| **Classe e objeto** | `Automoveis` é a classe; `a[i] = new Automoveis()` cria os objetos |
| **Atributos de instância** | `codigo`, `descricao`, `capacidadeTanque`, `litrosAbastecidos`, `kmRodada` |
| **Métodos de instância** | `consumo()`, `consumo(double)`, `classificacao()`, `mostrarDados()` |
| **Sobrecarga de métodos** | `consumo()` e `consumo(double litrosAbastecidos)` — mesmo nome, assinaturas diferentes |
| **Vetor de objetos** | `Automoveis a[] = new Automoveis[n]` — cada posição armazena uma referência |
| **Acumulador** | `totalLitrosAbastecidos += a[i].litrosAbastecidos` |
| **Maior valor** | Comparação `a[i].consumo() > melhorConsumo` dentro do loop |
| **Chamada de método dentro de método** | `classificacao()` chama `consumo()` internamente |
