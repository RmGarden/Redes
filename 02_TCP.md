# 🤝 TCP Handshake: Como os Computadores Dão as Mãos

Viste pacotes estranhos no Wireshark e ficaste com dores de cabeça? Vamos descomplicar!

Antes de dois computadores começarem a trocar dados a sério (carregar um site, jogar online ou enviar uma mensagem no Discord), eles precisam de estabelecer uma ligação segura. A este processo chamamos **TCP 3-Way Handshake** (o Aperto de Mão em 3 Passos).

---

## 🎭 O "Match" no Jogo Online

Imagina que tu e um amigo querem jogar online com chat de voz, mas antes de começarem a falar, precisam de garantir que os micros e auscultadores estão a funcionar:

1. **SYN (Synchronize):** Tu dizes no chat: *"Olá! Estás aí? Queres jogar? (Código: 100)"*
2. **SYN-ACK (Synchronize-Acknowledge):** O teu amigo responde: *"Ouvi o teu 100! Vamos jogar, para saberes que sou eu, confirma o meu código: 500."*
3. **ACK (Acknowledge):** Tu fechas a confirmação: *"Confirmado o teu 500! Tudo pronto, vamos a isso!"*

A partir deste momento, o canal está aberto e o jogo/transmissão pode começar!

---

## 🗺️ Da Vida Real ao Wireshark

```text
  [ CLIENTE / O Teu Computador ]                        [ SERVIDOR / O Jogo ou Web ]
                 |                                                   |
                 | ----- 1. SYN (Olá! Queres falar? Seq=100) ------> |
                 |                                                   |
                 | <--- 2. SYN-ACK (Recebido 100! E o meu 500?) ---- |
                 |                                                   |
                 | ----- 3. ACK (Recebido 500! Ligação OK) --------> |
                 |                                                   |
         ================== LIGAÇÃO ESTABELECIDA ==================
                 |                                                   |
                 | === Transmissão de Dados (HTTP, Discord, etc) ==> |

Como identificar no Wireshark:
Source (Origem): Quem está a enviar o pacote nesse passo.

Destination (Destino): Quem está a receber o pacote.

Info : Procura as etiquetas entre parênteses retos:

Passo 1: [SYN] ou [S]

Passo 2: [SYN, ACK] ou [S.]

Passo 3: [ACK] oou [A]

🧪 Quiz: "Master do Wireshark"
Testa os teus conhecimentos com este mini-quiz!

Pergunta 1: O Início da Conversa
Estás no Discord e queres mandar uma mensagem para um servidor.
Qual é a primeira flag TCP que o teu computador envia para abrir a conversa?

[ ] A) [ACK]

[ ] B) [SYN]

[ ] C) [FIN]


Pergunta 2: A Resposta Dupla
Quando o servidor recebe o teu [SYN],
como é que ele responde para dizer que ouviu o teu olá e que também quer falar contigo?

[ ] A) Envia apenas um [ACK]

[ ] B) Envia um [SYN, ACK]

[ ] C) Envia um [RESET]


Pergunta 3: Detetive do Wireshark
No Wireshark, estás a analisar um problema de ligação.
Vês os pacotes 1 (SYN) e 2 (SYN-ACK), mas o pacote 3 (ACK) nunca é enviado pelo cliente.
O que aconteceu?

[ ] A) A ligação foi estabelecida com sucesso.

[ ] B) O aperto de mão não terminou; a ligação não foi aberta e os dados não vão passar.

[ ] C) O servidor desligou-se imediatamente.

