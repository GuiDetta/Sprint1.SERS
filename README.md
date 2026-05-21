 # ChargeGrid Intelligence

 ## Vídeo

 https://youtu.be/6hMryOPBleU?si=kavgCcR3Zx9EGDqj

  ## Sobre o desafio

 A GoodWe é uma empresa de energia solar que também fabrica carregadores de carro elétrico. O carregador da linha HCA G2 hoje é um produto residencial, pensado para a garagem de uma casa: uma pessoa, um carro, uma conta de luz só. O desafio que ela trouxe para a FIAP foi outro: como transformar esse mesmo equipamento em um negócio para o comércio, ou seja, um lugar que
 recebe vários motoristas no mesmo dia.

 A gente escolheu como cenário o varejo de bairro (padaria, café, farmácia, mercadinho, academia), um conjunto de lojas pequenas de rua com 4 a 6 vagas. O cliente que para ali costuma ficar de 1 a 3 horas, tempo suficiente para uma recarga em corrente alternada.

  ## O problema

 Quando se leva o carregador residencial para um comércio, dois problemas aparecem:

 1. Não existe forma de cobrar pelo carregamento. O equipamento não distingue quem usou nem fatura a energia. Sem cobrança, não tem modelo de negócio.
 2. O risco da multa de demanda. Toda empresa contrata um limite de potência simultânea com a distribuidora. Se quatro carros começam a carregar ao mesmo tempo, esse limite estoura e o lojista paga uma multa pesada na conta de luz. É a dor real e ninguém comenta isso.

  A Resolução ANEEL nº 1.000/2021 (a agência do governo que regula energia elétrica) já permite explorar a recarga comercialmente, então não falta lei. Falta a tecnologia que ligue o carregador a essa operação.

  Na mentoria com a GoodWe de 13/05/2026 a empresa confirmou: ela não tem um modelo padrão de cobrança para o HCA G2, e o protocolo OCPP (Open Charge Point Protocol, o padrão aberto que normalmente cuida da cobrança em eletropostos) ainda não está disponível na linha HCA. Resolver isso é o que se espera do grupo, e é o que nossa solução faz.

 ## A solução: ChargeGrid Intelligence

 A proposta é instalar de 4 a 6 carregadores GoodWe na loja, conectá-los à placa solar e à bateria GoodWe que ficam no telhado, e amarrar tudo em uma plataforma de software que cuida de três coisas:

 - Cobrança automática: O motorista paga por Pix, cartão ou cartão RFID (Identificação por Radiofrequência, como o bilhete único do ônibus; ele só serve para autorizar a recarga na hora, a cobrança em si é uma camada nossa, pós-paga).
 - Gerenciamento de potência: O sistema distribui a energia entre os carros para não estourar o limite contratado pela loja.
 - Inteligência Artificial: Faz previsão de movimento, calcula um preço justo e gera relatórios para o dono da loja.

 ### O que diferencia a nossa proposta

 1. Recarga solar-aware. O carregador da GoodWe já tem dois modos de fábrica: "Prioridade Solar" e "FV + Bateria" (FV = fotovoltaica, ou seja, energia que vem do sol). A nossa plataforma usa esses modos e cria uma camada comercial em cima. Quando o sol está gerando, o motorista vê no aplicativo uma "tarifa Eco", mais barata. Todo mundo ganha: o motorista paga menos, a
 loja monetiza a energia solar que sobraria, e existe um discurso ambiental honesto.
 
 2. Bateria absorvendo o pico de carros. Quando vários carros chegam de uma vez, em vez de puxar tudo da rede e arriscar a multa, a plataforma usa a bateria GoodWe estacionária da loja para cobrir o aumento de consumo. Isso economiza dinheiro de verdade para o lojista todo mês.

 3. IA com função real. São quatro usos, com entrada e saída definidas:

 - Previsão de demanda: estima quantos carros vão chegar nas próximas 2 horas, com base em horário, dia da semana, clima e histórico do ponto.
 - Preço dinâmico: combina a geração solar do momento, a ocupação dos carregadores e a faixa horária da tarifa ANEEL para definir um preço. O preço é mostrado e aceito antes da sessão começar, e não muda no meio (é uma restrição da regulação).
 - Detecção de anomalia: identifica carro abandonado depois de carregar, falha na sessão, cartão usado de forma suspeita.
 - Assistente do lojista: traduz dados técnicos em linguagem normal, por exemplo: "seu pico de uso ontem foi entre 18h e 19h, vale subir 12% o preço nesse horário".

 ### O ganho real do lojista é tráfego, não a energia

 A receita da recarga em si é menor do que parece. O ganho de verdade vem do tempo que o cliente fica na loja. Quem para para carregar fica em média 75 minutos no local, contra cerca de 30 minutos de uma visita comum. Mais tempo no estabelecimento significa maior ticket médio. A divisão de receita da recarga, 70% para a loja e 30% para a operadora, serve para a loja não
 precisar investir nada no equipamento, não para ser a fonte principal de receita.

 ## Tecnologias usadas

 ### Hardware GoodWe

 - Inversor solar fotovoltaico GoodWe. É o equipamento que pega a energia que vem das placas solares e converte para a forma usada no consumo.                                                                                                                                                                                                                                    │
 - Bateria estacionária GoodWe da linha Lynx Home. Armazena energia e cobre o pico quando vários carros recarregam juntos. 
 - Vale comentar uma coisa que vimos no laboratório da FIAP: o carregador é de 7 kW, mas na prática entrega perto de 3,4 kW. Isso não é limitação dele, é do próprio carro, e para o nosso caso (cliente que fica 1 a 3 horas na loja) está de bom tamanho.

 ### Como o sistema se organiza

 A plataforma tem três camadas:

 - Camada Física: os carregadores, o inversor solar, a bateria e os medidores na loja.
 - Camada de Conectividade: a rede local e a internet (4G, Wi-Fi, LAN) que levam os dados até a nuvem.
 - Camada Digital: onde fica o motor de regras de potência, o módulo de IA, o gateway de pagamento e os painéis para lojista e motorista.

 ## Por que é uma proposta sustentável

 A sustentabilidade vem das escolhas técnicas que fizemos:

 - Aproveitar a energia solar na hora, no local. Usar essa energia ali mesmo, para carregar o carro do cliente, é mais eficiente do que mandá-la para a rede e tentar compensar depois.
 - A bateria reduz a pressão na rede nos horários de pico, quando a matriz elétrica costuma ser mais poluente.
 - Tornar a recarga comercial viável economicamente acelera a troca de carros a combustão por elétricos, o que reduz emissões de CO2 nas cidades.

 ### Modelo de negócio

 A ideia é um revenue share, ou seja, divisão da receita das recargas. A GoodWe instala o equipamento sem custo para o lojista, e os dois dividem o valor das recargas, com referência de 70% para o lojista e 30% para a GoodWe.

 A cobrança em si funciona pós-paga: o motorista se identifica, faz a recarga, e o valor é cobrado no Pix ou cartão depois. O preço é calculado antes da sessão e mostrado para o motorista aceitar; ele não muda durante a recarga, em respeito à regulação que foi citada na mentoria.
