> 1. Comentário: A Identidade da Engenharia de Software

```
O primeiro trecho do livro estabelece uma distinção fundamental entre o "fazer código" e a prática da engenharia. O autor defende que, embora os termos "Programação" e "Engenharia de Software" sejam usados como sinônimos, eles possuem pesos diferentes.

 O texto sugere que a programação, por si só, é uma atividade de construção que muitas vezes carece de rigor. A Engenharia de Software, por outro lado, é apresentada como a aplicação de conhecimento teórico para criar soluções **reais, precisas e seguras**. O ponto central é a necessidade de maturidade na indústria: assim como um engenheiro aeronáutico não pode errar cálculos sem causar desastres, o software moderno — que sustenta a vida em sociedade — exige métodos muito mais rigorosos do que a "programação tradicional".

```

> 2. Comentário: O Fator Tempo e Sustentabilidade

```
No segundo trecho, a definição de Engenharia de Software ganha uma dimensão temporal. 

 Análise: Enquanto a programação foca em resolver o problema imediato (escrever o código), a engenharia foca em "manter esse código valioso e funcional durante anos". Isso envolve processos, ferramentas e uma cultura organizacional que suporte a mudança. O sucesso não é apenas lançar o software, mas garantir sua SUSTENTABILIDADE: a capacidade de um sistema reagir a mudanças, escalar conforme a organização cresce e sobreviver ao ciclo de vida que vai desde a criação até a sua eventual desativação (depreciação).

```

> 3. Requisitos Não Funcionais

```
Diferente dos requisitos funcionais (o que o sistema faz), os não funcionais descrevem COMO o sistema deve ser.

1. Performance (Desempenho): Diz respeito à agilidade do sistema. Define, por exemplo, o tempo máximo que uma página pode levar para carregar ou a velocidade de processamento de um pedido.
2. Disponibilidade: É o tempo que o sistema permanece operável e acessível aos usuários. Um requisito comum é o "uptime" de 99,9%, garantindo que o serviço quase nunca fique fora do ar.
3. Escalabilidade: É a capacidade do software de suportar o aumento de demanda (mais usuários ou mais dados) sem degradar o serviço, seja adicionando mais memória ou mais servidores.
4. Segurança: Envolve a proteção do sistema contra acessos não autorizados e ataques, garantindo a integridade dos dados e a privacidade do usuário.
5. Usabilidade: Refere-se à facilidade com que um usuário consegue interagir com o sistema. Um software com boa usabilidade é intuitivo e exige pouco treinamento.

```

> 4. Cenários de Trade-offs

```
Um trade-off ocorre quando a melhoria de um requisito exige o sacrifício parcial de outro.

1. Segurança vs. Usabilidade:
   * Cenário: Um aplicativo bancário que exige biometria, senha e reconhecimento facial para qualquer ação.
   * Descrição: O sistema torna-se extremamente SEGURO, mas a USABILIDADE é prejudicada, pois o excesso de etapas torna a experiência do usuário lenta e cansativa.

2. Disponibilidade vs. Consistência:
   * Cenário: Um sistema de banco de dados distribuído em vários países durante uma falha de conexão.
   * Descrição: Se o sistema priorizar a CONSTANCIA, ele travará as atualizações até que todos os servidores concordem (ficando temporariamente indisponível). Se priorizar a DISPONIBILIDADE, ele permitirá o uso, mas usuários em locais diferentes podem ver informações levemente distintas por algum tempo.

3. Performance vs. Custo:
   * Cenário: Otimizar um site para responder em milissegundos utilizando servidores de altíssima potência.
   * Descrição: Para obter uma PERFORMACE excepcional, o engenheiro precisa investir em infraestrutura cara. O trade-off aqui é o ganho de velocidade em troca de um CUSTO FINANCEIRO muito mais elevado.

```

> 5. Programa com sintaxe correta, mas com a lógica errada (j+1=>j-1).

```

1.

# R: Não é possivel testar individualmente cada caso, pois existem 65535 casos de entrada;

2. Quantos erros apontam para o problema de lógica?

# R: 4

3. Quais são?

# R: -29999; 29999; -30000; e 30000.

```

> 6. Exercicio sobre um sistema de "Biblioteca" ( Usei um petshop para fazer a atividade ).

```

package BERTOTI;

import java.util.ArrayList;
import java.util.Scanner;

public class Petshop {
    public static void main(String[] args) {
        Scanner leitor = new Scanner(System.in);
        ArrayList<Pet> listaDePets = new ArrayList<>();
        int opcao = 0;

        System.out.println("--- Gestão de Pet Shop Java ---");

        do {
            System.out.println("\n1. Cadastrar Novo Pet");
            System.out.println("2. Listar Pets na Loja");
            System.out.println("3. Dar Banho em um Pet");
            System.out.println("4. Sair");
            System.out.print("Escolha uma opção: ");
            opcao = leitor.nextInt();
            leitor.nextLine(); // Limpar o buffer

            switch (opcao) {
                case 1:
                    System.out.print("Nome do Pet: ");
                    String nome = leitor.nextLine();
                    System.out.print("Espécie (Cão, Gato, etc): ");
                    String especie = leitor.nextLine();
                    listaDePets.add(new Pet(nome, especie));
                    System.out.println("Pet cadastrado com sucesso!");
                    break;

                case 2:
                    System.out.println("\n--- Lista de Espera ---");
                    if (listaDePets.isEmpty()) {
                        System.out.println("Nenhum pet no momento.");
                    } else {
                        for (int i = 0; i < listaDePets.size(); i++) {
                            System.out.println(i + ". " + listaDePets.get(i));
                        }
                    }
                    break;

                case 3:
                    System.out.print("Digite o índice do pet para o banho: ");
                    int index = leitor.nextInt();
                    if (index >= 0 && index < listaDePets.size()) {
                        Pet selection = listaDePets.get(index);
                        if (selection.isPrecisaDeBanho()) {
                            selection.setPrecisaDeBanho(false);
                            System.out.println(selection.getNome() + " tomou banho e agora está limpo!");
                        } else {
                            System.out.println("Este pet já está limpo!");
                        }
                    } else {
                        System.out.println("Pet não encontrado.");
                    }
                    break;
            }

        } while (opcao != 4);

        System.out.println("Sistema encerrado.");
        leitor.close();
    }
}


package BERTOTI;

public class Pet {
    private String nome;
    private String especie;
    private boolean precisaDeBanho;

    public Pet(String nome, String especie) {
        this.nome = nome;
        this.especie = especie;
        this.precisaDeBanho = true; // Todo pet chega precisando de um trato!
    }

    // Getters
    public String getNome() { return nome; }
    public String getEspecie() { return especie; }
    public boolean isPrecisaDeBanho() { return precisaDeBanho; }

    // Setter para atualizar o estado após o banho
    public void setPrecisaDeBanho(boolean precisaDeBanho) {
        this.precisaDeBanho = precisaDeBanho;
    }

    @Override
    public String toString() {
        String status = precisaDeBanho ? "[Sujeira detectada]" : "[Limpinho e Cheiroso]";
        return status + " " + nome + " (" + especie + ")";
    }
}


package BERTOTI;

import java.util.ArrayList;

public class HomologacaoPetshop {
    public static void main(String[] args) {
        ArrayList<Pet> bancoDadosFake = new ArrayList<>();

        // Simulando a inserção de múltiplos registros (como um INSERT no SQL)
        bancoDadosFake.add(new Pet("Bolinha", "Gato"));
        bancoDadosFake.add(new Pet("Thor", "Cão"));
        bancoDadosFake.add(new Pet("Nemo", "Peixe"));

        System.out.println("Verificando contagem de pets...");
        if (bancoDadosFake.size() == 3) {
            System.out.println("Sucesso: 3 pets inseridos no sistema.");
        } else {
            System.out.println("Falha: Contagem incorreta.");
        }

        // Testando busca por nome
        String busca = "Thor";
        for (Pet p : bancoDadosFake) {
            if (p.getNome().equals(busca)) {
                System.out.println("Sucesso: Pet '" + busca + "' encontrado no sistema.");
            }
        }
    }
}

```





 










