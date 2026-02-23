## 1. Comentário: A Identidade da Engenharia de Software
O primeiro trecho do livro estabelece uma distinção fundamental entre o "fazer código" e a prática da engenharia. O autor defende que, embora os termos **Programação** e **Engenharia de Software** sejam usados como sinônimos, eles possuem pesos diferentes.

* O texto sugere que a programação, por si só, é uma atividade de construção que muitas vezes carece de rigor. A Engenharia de Software, por outro lado, é apresentada como a aplicação de conhecimento teórico para criar soluções **reais, precisas e seguras**. O ponto central é a necessidade de maturidade na indústria: assim como um engenheiro aeronáutico não pode errar cálculos sem causar desastres, o software moderno — que sustenta a vida em sociedade — exige métodos muito mais rigorosos do que a "programação tradicional".

## 2. Comentário: O Fator Tempo e Sustentabilidade
No segundo trecho, a definição de Engenharia de Software ganha uma dimensão temporal. 

* **Análise:** Enquanto a programação foca em resolver o problema imediato (escrever o código), a engenharia foca em **manter esse código valioso e funcional durante anos**. Isso envolve processos, ferramentas e uma cultura organizacional que suporte a mudança. O sucesso não é apenas lançar o software, mas garantir sua **sustentabilidade**: a capacidade de um sistema reagir a mudanças, escalar conforme a organização cresce e sobreviver ao ciclo de vida que vai desde a criação até a sua eventual desativação (depreciação).

---

## 3. Requisitos Não Funcionais
Diferente dos requisitos funcionais (o que o sistema faz), os não funcionais descrevem **como** o sistema deve ser.

1. **Performance (Desempenho):** Diz respeito à agilidade do sistema. Define, por exemplo, o tempo máximo que uma página pode levar para carregar ou a velocidade de processamento de um pedido.
2. **Disponibilidade:** É o tempo que o sistema permanece operável e acessível aos usuários. Um requisito comum é o "uptime" de 99,9%, garantindo que o serviço quase nunca fique fora do ar.
3. **Escalabilidade:** É a capacidade do software de suportar o aumento de demanda (mais usuários ou mais dados) sem degradar o serviço, seja adicionando mais memória ou mais servidores.
4. **Segurança:** Envolve a proteção do sistema contra acessos não autorizados e ataques, garantindo a integridade dos dados e a privacidade do usuário.
5. **Usabilidade:** Refere-se à facilidade com que um usuário consegue interagir com o sistema. Um software com boa usabilidade é intuitivo e exige pouco treinamento.

---

## 4. Cenários de Trade-offs
Um trade-off ocorre quando a melhoria de um requisito exige o sacrifício parcial de outro.

1. **Segurança vs. Usabilidade:**
   * **Cenário:** Um aplicativo bancário que exige biometria, senha e reconhecimento facial para qualquer ação.
   * **Descrição:** O sistema torna-se extremamente **Seguro**, mas a **Usabilidade** é prejudicada, pois o excesso de etapas torna a experiência do usuário lenta e cansativa.

2. **Disponibilidade vs. Consistência:**
   * **Cenário:** Um sistema de banco de dados distribuído em vários países durante uma falha de conexão.
   * **Descrição:** Se o sistema priorizar a **Consistência**, ele travará as atualizações até que todos os servidores concordem (ficando temporariamente indisponível). Se priorizar a **Disponibilidade**, ele permitirá o uso, mas usuários em locais diferentes podem ver informações levemente distintas por algum tempo.

3. **Performance vs. Custo:**
   * **Cenário:** Otimizar um site para responder em milissegundos utilizando servidores de altíssima potência.
   * **Descrição:** Para obter uma **Performance** excepcional, o engenheiro precisa investir em infraestrutura cara. O trade-off aqui é o ganho de velocidade em troca de um **Custo Financeiro** muito mais elevado.
