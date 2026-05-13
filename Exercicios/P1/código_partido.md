# Análise de Código — Sistema de Cadastro e Avaliação de Partidos Políticos

Este programa cadastra partidos políticos, verifica se atingiram o mínimo de assinaturas exigido e exibe relatórios de aprovação e classificação.

---

## Classe `Partido`

Representa a entidade "Partido Político" com seus atributos e comportamentos.

```java
class Partido {

    // Atributos de instância — cada objeto Partido terá seus próprios valores
    int codigo;       // Código identificador do partido
    int filiados;     // Quantidade de membros filiados
    String descricao; // Nome/descrição do partido
    String presidente;// Nome do presidente do partido
    float assinaturas;// Quantidade de assinaturas coletadas

    // Método aprovado() sem parâmetro — sobrecarga (versão com valor fixo)
    // Retorna true se assinaturas >= 491.656 (mínimo legal fixo)
    public boolean aprovado() {
        return this.assinaturas >= 491656;
    }

    // Método aprovado(float) — sobrecarga (versão com mínimo variável)
    // Recebe o mínimo por parâmetro, permitindo uso dinâmico
    public boolean aprovado(float minimo) {
        return this.assinaturas >= minimo; // Compara assinaturas com o mínimo recebido
    }

    // Método classificacao() — retorna uma string com a classificação do partido
    // Baseada na proporção entre assinaturas e o mínimo exigido
    public String classificacao(float minimo) {

        float indice = this.assinaturas / minimo; // Calcula o índice proporcional (0.0 a 1.0+)

        if (this.aprovado(minimo)) return "Satisfatorio"; // Atingiu ou superou o mínimo
        if (indice >= 0.75)        return "Insatisfatorio"; // Entre 75% e 99% do mínimo
        if (indice >= 0.50)        return "Ruim";           // Entre 50% e 74% do mínimo
        if (indice >= 0.25)        return "Muito ruim";     // Entre 25% e 49% do mínimo
        return "Péssimo";                                   // Abaixo de 25% do mínimo
    }

    // Método mostrarDados() — exibe todos os atributos do partido no console
    public void mostrarDados() {
        System.out.println(
            "Codigo: "     + this.codigo    +
            "\nDescricao: " + this.descricao +
            "\nPresidente: " + this.presidente +
            "\nFiliados: "  + this.filiados  +
            "\nAssinaturas: " + this.assinaturas
        );
    }
}
```

---

## Classe `LerPartido`

Classe principal com o método `main`. Responsável pela entrada de dados, processamento e exibição dos resultados.

```java
class LerPartido {

    public static void main(String[] args) throws Exception {

        // Declaração das variáveis de controle
        float minimo;          // Mínimo de assinaturas informado pelo usuário
        int soma = 0;          // Acumulador: soma de filiados dos partidos aprovados
        int maior = 0;         // Maior número de filiados entre TODOS os partidos
        int maiorAprov = 0;    // Maior número de filiados entre os partidos APROVADOS
        String nomeMaior = ""; // Nome do partido com mais filiados no geral
        String nomeAprov = ""; // Nome do partido aprovado com mais filiados

        // Solicita e lê o mínimo de assinaturas exigido
        System.out.print("Minimo: ");
        minimo = JUtil.readFloat(); // Lê um float do teclado via classe utilitária JUtil

        // Solicita a quantidade de partidos e cria o vetor de objetos Partido
        System.out.print("Quantos: ");
        Partido p[] = new Partido[JUtil.readInt()]; // Cria vetor com tamanho informado pelo usuário

        // Loop de cadastro — percorre cada posição do vetor
        for (int i = 0; i < p.length; i++) {

            p[i] = new Partido(); // Instancia um novo objeto Partido na posição i

            // Lê e armazena os dados do partido
            System.out.print("Codigo: ");
            p[i].codigo = JUtil.readInt();

            System.out.print("Nome: ");
            p[i].descricao = JUtil.readString();

            System.out.print("Presidente: ");
            p[i].presidente = JUtil.readString();

            System.out.print("Filiados: ");
            p[i].filiados = JUtil.readInt();

            System.out.print("Assinaturas: ");
            p[i].assinaturas = JUtil.readFloat();

            // Verifica se o partido foi aprovado (atingiu o mínimo)
            if (p[i].aprovado(minimo)) {

                soma += p[i].filiados; // Acumula os filiados dos aprovados

                // Atualiza o partido aprovado com maior número de filiados
                if (p[i].filiados > maiorAprov) {
                    maiorAprov = p[i].filiados;  // Guarda o novo maior valor
                    nomeAprov = p[i].descricao;  // Guarda o nome correspondente
                }
            }

            // Atualiza o partido com maior número de filiados (independente de aprovação)
            if (p[i].filiados > maior) {
                maior = p[i].filiados;      // Guarda o novo maior valor geral
                nomeMaior = p[i].descricao; // Guarda o nome correspondente
            }
        }

        // Loop de exibição — imprime os dados de todos os partidos cadastrados
        for (int i = 0; i < p.length; i++) {
            System.out.println(
                "\n" + p[i].descricao +                        // Nome do partido
                " | Filiados: "    + p[i].filiados +           // Quantidade de filiados
                " | Assinaturas: " + p[i].assinaturas +        // Assinaturas coletadas
                " | " + (p[i].aprovado(minimo) ? "Aprovado" : "Nao") + // Status de aprovação
                " | " + p[i].classificacao(minimo)             // Classificação (Satisfatório, Ruim, etc.)
            );
        }

        // Exibe os resultados finais consolidados
        System.out.println("\nSoma aprovados: " + soma);          // Total de filiados dos aprovados
        System.out.println("Maior: " + nomeMaior + " - " + maior);            // Partido com mais filiados
        System.out.println("Maior aprovado: " + nomeAprov + " - " + maiorAprov); // Aprovado com mais filiados
    }
}
```

---

## Resumo dos Conceitos Aplicados

| Conceito | Onde aparece |
|---|---|
| **Classe e objeto** | `Partido` é a classe; `p[i] = new Partido()` cria os objetos |
| **Atributos de instância** | `codigo`, `filiados`, `descricao`, `presidente`, `assinaturas` |
| **Métodos de instância** | `aprovado()`, `aprovado(float)`, `classificacao()`, `mostrarDados()` |
| **Sobrecarga de métodos** | `aprovado()` e `aprovado(float minimo)` — mesmo nome, assinaturas diferentes |
| **Vetor de objetos** | `Partido p[] = new Partido[n]` — cada posição armazena uma referência |
| **Operador ternário** | `p[i].aprovado(minimo) ? "Aprovado" : "Nao"` |
| **Acumulador** | `soma += p[i].filiados` |
| **Maior valor** | Comparação dentro do loop para `maior` e `maiorAprov` |
