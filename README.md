# bip39-bruteforce-fork
Great job Written by @EddieOz 

https://medium.com/@eddieoz/generosidade-criptografada-6aabea16061d


Generosidade Criptografada
A Jornada Inusitada para Resgatar uma Doação através da Recuperação de uma Chave Privada
@EddieOz
@EddieOz

·
Follow

5 min read
·
1 day ago
63




Na semana passada, uma mensagem inesperada chegou até mim, lançando luz sobre um dilema que um membro da comunidade estava enfrentando com sua hardware wallet. A mensagem carregava um tom de esperança renovada, uma chance de resgatar algo que parecia irremediavelmente perdido.

“Eddie, estou aqui novamente. Já faz um tempo que perdi cerca de meio bitcoin em uma carteira da qual perdi a chave privada. Conversando com a comunidade do BLOCO, surgiu a ideia de entrar em contato contigo para fazer uma transmissão ao vivo tentando quebrar a chave. Se conseguirmos acessar os fundos, estou disposto a doar o valor para o MC. Seria ótimo discutir mais detalhes sobre essa ideia. Já trocamos algumas mensagens, mas nunca tivemos a oportunidade de falar pessoalmente, o que seria uma grande honra e prazer.”


A proposta era audaciosa, mas a promessa de uma doação generosa para o Morning Crypto (MC) acendeu uma chama de entusiasmo em mim. No entanto, eu sabia que a jornada não seria fácil. O processo de recuperação da chave privada é trabalhoso e demorado, e poderia potencialmente expor informações sensíveis ao público caso fosse feita ao vivo.

Com mais de 25 anos de experiência em cybersegurança e uma paixão por desvendar puzzles criptográficos, eu estava mais do que pronto para aceitar o desafio. Ao longo dos anos, participei de vários desafios de pentest em black box e buscas por bitcoins escondidos, tendo obtido sucesso em várias ocasiões.

O Processo
O primeiro passo foi coletar todas as informações possíveis sobre a wallet, incluindo o endereço onde os fundos foram depositados e qualquer fragmento da seed que ele ainda possuía. Felizmente, ele tinha anotado algumas palavras, embora três delas não estivessem listadas na BIP39, sugerindo um possível erro de anotação durante a configuração inicial da wallet Ledger Nano.

Em um mundo onde cada detalhe pode ser a chave para desvendar um mistério, sabia que precisava explorar todas as possibilidades. Com base na ampla documentação disponível sobre como a Ledger trabalha com a BIP39 e a validação por dígito verificador, comecei a desenvolver um plano.

Recorri a recursos online e ao meu próprio arsenal de códigos antigos para criar um script em Python que pudesse acelerar o processo. Inspirado por um desafio semelhante proposto por Alistair Milne no Twitter há alguns anos e solucionado por John Cantrel, comecei a codificar, focando em três aspectos cruciais: o endereço de depósito dos fundos, a seed incompleta e o tipo de hardware wallet utilizada.

Durante o processo, percebi que a Ledger tinha uma peculiaridade que poderia ser vista como uma falha de UX: algumas palavras se assemelhavam muito no visor, facilitando confusões por usuários mais desatentos.

Dediquei um tempo significativo à pesquisa de parônimos que poderiam gerar confusão na interface da Ledger, identificando palavras potenciais candidatas que poderiam auxiliar na economia de tempo valioso de processamento.

Após uma fase inicial de preparação detalhada, iniciei a programação, desenvolvendo múltiplas versões do script para aprimorar tanto a performance quanto a eficiência, explorando desde técnicas de processamento paralelo até a utilização de GPU. A segunda iteração do script incorporou o processo em threads, no entanto, não apresentou um desempenho satisfatório no meu computador. A terceira versão, por sua vez, empregou a paralelização do processamento, uma estratégia que se mostrou bastante promissora, especialmente quando considerando a implementação em uma infraestrutura distribuída.

A concepção final, embora posteriormente descartada, visava executar todas as operações na GPU, inicialmente através do PyTorch-cuda e, posteriormente, utilizando o OpenCL no meu sistema Linux. Este enfoque, no entanto, exigiria um investimento considerável no desenvolvimento dos kernels para o SHA256, bem como para os protocolos BIP32 e BECH32. A despeito da magnitude da tarefa — mais de 8,5 bilhões de interações, especificamente 8.589.934.592, uma cifra significativamente menor que o desafio enfrentado por John Cantrel (1 trilhão de interações) — mantinha a confiança de que, com a identificação de parônimos promissores, seria possível reduzir alguns milhões de interações potenciais.

A jornada foi árdua, com várias tentativas falhando em encontrar as wallets corretas. Mas, com persistência e uma expansão gradual do escopo de busca, finalmente encontrei uma lista de seeds candidatas, válidas, que continham mais de 10,7 milhões de endereços segwit nativos.

O momento da verdade chegou, e com o coração pulsando forte, executei o script de busca. A emoção tomou conta quando os endereços foram encontrados com sucesso, marcando o fim de um fim de semana intenso e o início de uma celebração merecida.

Os scripts criados podem ser encontrados no meu github.

Conclusão e Dicas Valiosas
Esta jornada não apenas resultou em vitória, mas também serviu como um lembrete poderoso da importância da segurança e da auto-custódia no mundo das criptomoedas. Para ajudar a evitar tais transtornos no futuro, gostaria de compartilhar algumas dicas que destaco frequentemente no Morning Crypto:

Anote sempre as palavras da sua seed em papel, preferencialmente em metal, como discutido em alguns episódios do programa.
Após configurar sua hardware wallet, resete-a e recupere a seed por inteiro para evitar situações como a descrita acima.
Considere ter mais de uma hardware wallet para contingências.
Mantenha backups da sua seed em locais distintos; uma única cópia não é suficiente.
Lembre-se: “Not your keys, not your coins”. As exchanges não são bancos, nem carteiras seguras, nem suas amigas.
Pratique a auto-custódia, uma ferramenta vital para preservar a sua liberdade, autonomia e soberania financeira no mundo digital.
Gostaria de expressar minha profunda gratidão ao generoso membro da comunidade que confiou em mim para resolver este desafio.

Sobre o autor
Edilson Osorio Jr. é um renomado founder, cientista da computação, professor e especialista em segurança da informação e infraestrutura. Reconhecido pela CoinTelegraph como a personalidade mais importante e influente no campo das criptomoedas e blockchain no Brasil, Edilson consolidou um nicho significativo no ecossistema cripto.

Ao longo de sua ilustre carreira, ele acumulou inúmeros prêmios e reconhecimentos, incluindo o Desafio de Impacto Social do Google.org em 2016, Personalidade Financeira do Ano em 2017, e sendo nomeado o Campeão Global nº 1 em Cibersegurança no AIM — Annual Investing Meeting em Dubai em 2020, seguido de um Leão de Bronze no Festival de Cannes em 2021 e, mais recentemente, foi escolhido como e-Residency Envoy pelo governo Estoniano em 2023, entre muitos outros prêmios.

Em 2021, Edilson embarcou em uma nova empreitada, lançando o programa “Morning Crypto”, uma transmissão diária que rapidamente se tornou um dos mais confiáveis veículo de notícias no ecossistema cripto. O programa, que está se aproximando de seu 500º episódio, oferece uma rica mistura de discussões sobre regulamentações governamentais, inovações tecnológicas, tendências de mercado e entrevistas com especialistas da indústria, tudo isso acompanhado de entretenimento interativo em tempo real. Transmitido em plataformas como kick.com, YouTube e Nostr, o programa fomentou uma comunidade vibrante e engajada conhecida como BLOCO.

Para se manter atualizado com suas percepções e as últimas novidades no mundo das criptomoedas, siga Edilson em:

X.com: @eddieoz
Kick.com: @eddieoz
YouTube: @eddieoz
Instagram: @_eddieoz
Nostr: eddieoz@sats4.life
Github: @eddieoz
Com uma paixão inabalável por inovação e um compromisso com a excelência, Edilson continua sendo um farol de inspiração e liderança na indústria de cybersegurança, criptomoedas e blockchain.

