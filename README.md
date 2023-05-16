# Projeto final - macroentrega 3

## Sobre o projeto 

O projeto foi divido em 3 partes (macroentregas):
1. * Macroentrega 1: leitura de arquivo e verificar soluções geradas
2. * Macroentrega 2: resolução do Problema do Caixeiro Viajante
3. * Macroentrega 3: estatística descrittiva dos dados (soluções) geradas pelo algoritmo da  macroentrega 2.

* **O foco deste repositório é a macroentrega 3**

* Contextualizando: Ao analisarmos o problema referente à Macroentrega 2, identificamos como uma “variação” do Problema do Caixeiro-Viajante (PCV), onde temos que: partir de um ponto de origem (depósito), traçar uma rota na qual passamos pelos pontos de coleta e, após isso, passar pelos seus respectivos pontos de entrega e, ao final, voltar ao ponto de origem, isso passando pela menor rota possível. Entretanto, há mais uma variável a ser considerada, as janelas de tempo, tanto do depósito, quanto do ponto de coleta, quanto do cliente. Por conta dessa variável a ser considerada, torna-se uma “variação” do PCV. Pelo fato de as arestas serem ponderadas com o tempo, temos que além de traçar a menor rota, obedecer às janelas de tempo. Pensando de modo simplista, seria somente usar vários caminhões e resolver o problema, mas temos que considerar também a menor quantidade de caminhões possíveis. Dessa forma, temos que fazer com que cada caminhão seja usado da melhor maneira possível. 

* O algoritmo que resolve este problema, foi implementado na macroentrega 2. **O foco deste repositório é a macroentrega 3**, onde é feita uma estatística descritiva das saídas, realizando a visualização de dados da comparação com os resultados obtidos pelo nosso algoritmo de resolução do problema (macroentrega 2) com os resultados ótimos (que não é possível ser melhor).

## Descrição melhor detalhada do problema (Não é necessário ler, somente caso queira entender melhor o que é o problema)
Durante a pandemia, a demanda por serviços logísticos cresceu em virtude do aumento de compras online (Fonte: [“Logística cresce na pandemia com aumento de compras pela internet”, por Paula Monteiro, em Pequenas Empresas & Grandes Negócios](https://g1.globo.com/economia/pme/pequenas-empresas-grandes-negocios/noticia/2021/01/31/logistica-cresce-na-pandemia-com-aumento-de-compras-pela-internet.ghtml)). Grandes empresas que realizam suas operações de entregas de produtos buscam sempre uma redução de custos logísticos, a fim de utilizar tal economia de recursos em outros investimentos de interesse corporativo. Um dos problemas mais comuns nesses contextos é descrito formalmente abaixo.

Considere que uma empresa possua uma frota de veículos M e um conjunto de clientes C a serem atendidos. O deslocamento dos veículos pode ser modelado através de um grafo direcionado $G = (V, A)$. O conjunto de vértices do grafo pode ser representado por $V = P \cup D \cup \\{0\\}$, em que $P$ representa o conjunto de pontos de coleta, $D$ o conjunto de pontos de entrega e 0 representa o depósito. O conjunto de arcos é denotado por A, e representa as conexões entre os vértices, seja depósito ou clientes. A cada arco $(i, j)$, $i \ne j$, associa-se um custo $c_{ij}$ e um tempo $t_{ij}$.
Assume-se que os tempos de deslocamento respeitam a desigualdade triangular $(\forall i,j,k \in V, t_{ij} \le t_{ik}+t_{kj})$. Considera-se que o custo de deslocar-se entre $i$ e $j$ é diretamente proporcional ao tempo de deslocamento entre $i$ e $j$.

Cada veículo $m$ tem uma capacidade $q_m$, enquanto cada ponto $i$ possui uma demanda $d_i$ e um tempo de serviço, para ser atendido, denotado por $s_i$. Em um pedido $r=(i,j),i \in P,j \in D$, assume-se que $d_i \ge 0$ e que $d_i + d_j = 0$. Cada cliente $i$ tem uma janela de tempo $\[𝑎_i, 𝑏_i]$. Um veículo deve chegar ao cliente antes do tempo $b_i$. Pode ser que um veículo chegue ao cliente $i$ antes do tempo $a_i$. No entanto, o cliente não será atendido antes desse instante. O depósito também possui uma janela de tempo $\[𝑎_0, 𝑏_0]$. Os veículos não podem sair do depósito antes de $a_0$ e devem estar de volta antes ou no horário $b_0$. Adota-se os seguintes valores para a janela de tempo de depósito: $a_0 = 0$ e $b_0 = 0$, em que $H$ é o horizonte de tempo da roteirização.

Uma solução factível (ou viável) para tal problema deve respeitar as restrições apresentadas a seguir.
1. **precedência de coleta e entrega:** para um pedido $r = (i, j)$, em que $i$ e $j$ são seus respectivos pontos de coleta e entrega, o ponto de entrega $j \in D$ não pode ser visitado antes de seu correspondente ponto de coleta $i \in P$.
2. **origem e horário de serviço:** cada veículo $f \in \\{1,...,m\\}$ deve partir e retornar do ponto de origem $0$ no intervalo da janela de tempo $\[𝑎_0, 𝑏_0]$.
3. **janelas de tempo:** O tempo de chegada do veículo $f \in \\{1,...,m\\}$ ao ponto $i \in V$ não pode exceder $b_i$. Caso o motorista do veículo $f \in \\{1,...,m\\}$ chegue antes de $a_i$, o mesmo deve esperar até $a_i$ para realizar o atendimento do ponto.
4. **obrigatoriedade e exclusividade de visita:** para cada pedido $r=(i,j)$, seus pontos de coleta e entrega devem ser visitados exatamente uma vez.
5. **atendimento de pedido:** em um pedido $r=(i,j)$, a visita ao ponto $i \in P$ por um veículo $f \in \\{1,...,m\\}$ torna obrigatório que o atendimento ao ponto $j \in D$ seja feito pelo mesmo veículo.
6. **capacidade do veículo:** o somatório das demandas referentes aos pontos atendidos por um veículo $f \in \\{1,...,m\\}$ não pode ultrapassar a capacidade do veículo, denotada por $q_m$.

A função objetivo a ser otimizada é hierarquicamente definida por:
1. **Minimização da quantidade de veículos** utilizada para atender todos os
pedidos, respeitando as restrições do problema.
2. **Minimização do custo total** gasto por todas as rotas.

## Objetivos

Desenvolva um algoritmo eficiente, que retorne uma solução viável para o problema descrito acima. Para tanto, as linguagens de programação C++ e Python podem ser utilizadas.

## Base de Dados (Não é necessário ler, somente caso queira saber melhor o que tem em cada instância)
Trinta instâncias foram selecionadas da literatura para a seção de experimentos computacionais deste trabalho.

As primeiras 10 linhas de cada arquivo contém informações gerais sobre a instância:
- $NAME$: \<identificação de instância única>
- $LOCATION$: \<cidade onde foi gerado>
- $COMMENT$: \<uma referência geral>
- $TYPE$: \<o tipo da instância>
- $SIZE$: \<número de vértices incluindo o depósito>
- $DISTRIBUTION$: \<distribuição a qual a instância foi gerada>
- $DEPOT$: \<tipo de localização do depósito: 'central' ou 'aleatório'>
- $ROUTE-TIME$: \<horizonte de tempo da roteirização>
- $TIME-WINDOW$: \<largura da janela de tempo>
- $CAPACITY$: \<capacidade máxima do veículo>

Após a linha com a palavra “NODES”, é seguida por uma quantidade SIZE de linhas, contendo as informações completas de cada ponto (vértice) no arquivo de instância. Para cada linha, existem 9 campos separados por um único caractere de espaço em branco como abaixo: _\<id>_ _\<lat>_ _\<long>_ _\<dem>_ _\<etw>_ _\<ltw>_ _\<dur>_ _\<p>_ _\<d>_.
  
Os campos são:
- _\<id>_: o identificador único do ponto (o ponto 0 é o depósito único);
- _\<lat>_: latitude deste local;
- _\<long>_: longitude deste local;
- _\<dem>_: a demanda deste nó (dem > 0 para coleta, dem < 0 para entrega);
- _\<etw>_: tempo mais cedo possível para iniciar o serviço (janela de tempo);
- _\<ltw>_: última hora possível para iniciar o serviço (janela de tempo);
- _\<dur>_: a duração do serviço neste local;
- _\<p>_: o par de coleta se <id> for uma entrega; e 0 caso contrário;
- _\<d>_: o par de entrega se <id> for uma coleta; e 0 caso contrário

O _\<p>_ e _\<d>_ são apenas para fins de integridade. Em todas as instâncias, para um local de coleta _\<id>_ sua entrega é dada por $(<id>+((SIZE-1)/2))$. Para um local de entrega _\<id>_, sua coleta é dada por $(<id>-((SIZE-1)/2))$.
  
Após todos os NODES, existe uma linha contendo a palavra EDGES seguida de $SIZE$ linhas, cada uma com $SIZE$ valores inteiros separados por um único espaço em branco. Esses números inteiros representam os tempos de viagem entre cada par de locais na instância, medidos em minutos e calculados usando o Ferramenta [Open Source Routing Machine (OSRM)](https://project-osrm.org).

Todas as instâncias terminam com uma linha contendo a palavra EOF.

## O que foi pedido na Macroentrega 3: 

### Implementação de interface via Google Colab para interação e visualização das soluções 

A interface de seu programa deve ser disponibilizada por meio do Google Colab. No notebook, o usuário deve ter a opção de fazer o upload de um arquivo. O processamento do algoritmo deve ocorrer chamando o seu projeto dentro do Colab. Ao imprimir sua resposta, utilize uma ferramenta para visualização da solução, tal como Google My Maps. As estatísticas relativas à solução podem ser exibidas por meio de dashboards, utilizando as bibliotecas pandas ou ploty, por exemplo.

Seja criativo na exibição das informações do dashboard. Algumas ideias: 
* Quantidade de veículos utilizados; 
* Custo total do trajeto realizado por todos os veículos utilizados; 
* Tempo ocioso de cada veículo (quando o veículo chega antes da janela de tempo, ou quando chega antes do tempo de fechamento do depósito); 
* Maior e menor distância percorrida por cada veículo considerando cada par de pontos visitados na sequência

## Como executar

requisitos: ter conta no Google Colab

* Antes de tudo, baixe este repositório na sua máquina. Isso é possível clicando no botão verde, escrito "code", localizado no canto superior direito acima do repositório e depois clicando em "download zip", ou dê um git clone neste repositório.

* Abra o Google Colab (https://colab.research.google.com/), vá em Arquivo -> Abrir notebook -> Upload. Após ter **descompactado** a pasta deste repositório, coloque ou o código ``graphic_m3`` ou o ```map_ploting_m3`` no campo de Upload do Colab.

### Para executar o ``graphic_m3``

1. * Coloque o arquivo disponibilizado neste repositório chamado "report.csv" na parte de arquivos do Google Colab ou da IDE que estiver usando. 
2. * Rode o script do Colab bloco por bloco, **desde o início**, para que as saídas saiam organizadas e para que sua visualização seja melhor. Ou apenas clique em Ambiente de execução -> Executar tudo.
3. * Enfim, siga as intruções dadas durante a execução do código

### Para executar o ``map_ploting_m3``

1. * Baixe a pasta disponibilizada neste repositório chamada "outputs".
2. * Abra a pasta "outputs", selecione uma instância e coloque-a na parte de arquivos do Google Colab ou da IDE que estiver usando, não coloque a pasta toda, pois o Colab não suporta. (É recomendado que pegue instâncias menores, o número de pontos de entrega e coleta está no nome do arquivo, bar1-**n100**, por exemplo, possui 100 pontos de coleta e entrega, o que é uma pequna quantidade e ficará viável de se visualizar).
3. * Digite o nome da instância (arquivo que você colocou na pasta do Colab) quando for pedido, seguindo o exemplo fornecido, para que o programa possa realizar os mapas. 
4. * Rode o script do Colab bloco por bloco, **desde o início**, para que as saídas saiam organizadas e para que sua visualização seja melhor. Ou apenas clique em Ambiente de execução -> Executar tudo.
5. * Enfim, **siga as intruções dadas durante a execução do código**.

#### ***Observação: os arquivos das rotas geram um html, então é necessário fazer o download dos arquivos gerados e abrí-los. Eles ficam na parte de arquivos do Colab***

## Exemplo de algumas saídas geradas por estes algoritmos (caso não tenha experiência com Google Colab)

Todas as saídas geram um html onde é possível interagir com o gráfico ou mapa, disponibilizei exemplos desses html's no repositório 

### Saídas do ``graphic_m3``:

![newplot (2)](https://github.com/s4bino/macro3-grafos/assets/121155839/bc81872f-8326-4ee3-82bd-be771af4dfd1)

![newplot (3)](https://github.com/s4bino/macro3-grafos/assets/121155839/d71bd0fa-a57f-4b92-9bd5-a185f8307006)


## Saídas do ``map_ploting_m3``:

### pontos de entrega e coleta
![image](https://github.com/s4bino/macro3-grafos/assets/121155839/6950b6f8-e309-4972-877b-968c5997a2e2)

### rota de 1 caminhão

![image](https://github.com/s4bino/macro3-grafos/assets/121155839/129b5598-5fd9-4ae9-89cc-574df6060705)

### mapa de calor dos pontos de entrega

![image](https://github.com/s4bino/macro3-grafos/assets/121155839/c37f9794-b84c-469c-bb70-53f75e485515)


