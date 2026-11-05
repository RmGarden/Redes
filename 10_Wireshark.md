# 🦈Wireshark 
## O Raio-X e o Inspetor de Correio da Rede

Imagina que os computadores da tua rede estão a trocar milhões de cartas e encomendas todos os segundos.  
Se algo correr mal (um site que não abre, um jogo com *lag* ou uma app que falha), como é que descobres o que se está a passar lá dentro? 

É aqui que entra o **Wireshark**, a ferramenta definitiva de análise de redes!

---

## 🕵️O Inspetor Postal com Visão de Raio-X

Pensa no **Wireshark** como um **inspetor de correio ultra-especializado** sentado no meio da central de correios da tua rede:
* Normalmente, as cartas passam pelos tubos e tu só vês o exterior (o envelope com o remetente e o destinatário).
* Com o Wireshark ativado, o inspetor consegue **interceptar uma cópia de todas as cartas**, abri-las com cuidado e mostrar-te exatamente o que está escrito lá dentro, palavra por palavra.
* Ele consegue mostrar-te o pacote desde a "caixa exterior" (Camada 2 - Ethernet) até à "carta de amor ou fatura" que vai lá dentro (Camada 7 - Aplicação, como HTTP, DNS ou chat).

---

## 🔍O Que Consegues Ver com o Wireshark?

Quando abres o Wireshark e começas a "capturar" o tráfego da tua placa de rede, o ecrã enche-se de linhas coloridas. Cada linha é um pacote de dados a passar.  
O programa divide a informação em **três janelas principais**:

1. **A Lista de Pacotes:**  
Mostra um resumo de cada pacote capturado (o número, a hora exata, o IP de origem, o IP de destino, o protocolo e uma breve descrição).

2. **Os Detalhes do Pacote:**  
Permite "abrir" o pacote por camadas (como se fossem as bonecas russas Matrioskas), mostrando a camada física, de rede, de transporte e de aplicação.

3. **O Hexadecimal / Bytes:**  
Mostra o código bruto em formato binário/hexadecimal do que está a viajar fisicamente pelo cabo ou Wi-Fi.

---

## 🚦O Super-Poder dos Filtros

Como passam milhares de pacotes por segundo no teu computador, o Wireshark tem um campo de **Filtros** mágico no topo.  
Em vez de veres tudo, podes ordenar ao inspetor para mostrar apenas o que te interessa:
* Escrever `dns` $\rightarrow$ Mostra apenas os pedidos e respostas de nomes de sites.
* Escrever `ip.addr == 140.82.114.3` $\rightarrow$ Mostra apenas o tráfego enviado ou recebido desse IP específico (ex: GitHub).
* Escrever `tcp.port == 80` $\rightarrow$ Mostra apenas o tráfego web não encriptado.

---
# 🔬 Casos Práticos

Nada melhor do que ver o Wireshark em ação com exemplos práticos do dia a dia. Aqui tens três cenários comuns que vais conseguir identificar facilmente assim que começares a capturar pacotes!

---

## 🚦 Cenário 1: 
## O TCP Handshake em Ação

Lembras-te daquela conversa de amizade entre computadores (SYN $\rightarrow$ SYN-ACK $\rightarrow$ ACK)?  
No Wireshark, podes vê-la acontecer exatamente assim na tabela de pacotes:

| No. | Tempo | Origem | Destino | Protocolo | Comprimento | Informação |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 0.000 | `192.168.1.15` | `140.82.114.3` | TCP | 74 | `54321 → 443 [SYN] Seq=0 Win=64240 Len=0` |
| 2 | 0.015 | `140.82.114.3` | `192.168.1.15` | TCP | 74 | `443 → 54321 [SYN, ACK] Seq=0 Ack=1 Win=65160 Len=0` |
| 3 | 0.016 | `192.168.1.15` | `140.82.114.3` | TCP | 66 | `54321 → 443 [ACK] Seq=1 Ack=1 Win=64240 Len=0` |

 **O que estás a ver aqui?**
O teu computador (`.15`) envia um sinal `SYN` (olá!), o servidor do GitHub responde com `SYN, ACK` (olá de volta, aceito!) e o teu computador confirma com `ACK` (ótimo, vamos começar a falar!). 

---

## 🔍 Cenário 2: 
## Uma Consulta DNS Real (`Apanhar o Nome`)

Se filtrares o Wireshark por `dns`, vais ver exatamente o momento em que o teu browser pergunta por um site:

| No. | Protocolo | Informação |
| :--- | :--- | :--- |
| 12 | **DNS** | `Standard query 0x1a2b A github.com` *(O teu PC a perguntar o IP)* |
| 13 | **DNS** | `Standard query response 0x1a2b A github.com Addr 140.82.114.3` *(O servidor a responder com o IP)* |

 **O que estás a ver aqui?**
O pacote #12 é o pedido (*Query*) em formato texto legível, e o pacote #13 traz a resposta oficial com o endereço IP numérico que o computador precisava para ligar o motor.

---

## 🔓 Cenário 3: 
## HTTP vs. HTTPS

* **Se entrares num site antigo que usa HTTP (porta 80):**
* O Wireshark consegue ler o texto **todo em claro**. Se escreveres a tua password num formulário de login desprotegido, qualquer pessoa com o Wireshark ligado na mesma rede Wi-Fi pública consegue ver a tua palavra-passe escrita exatamente como tu a digitaste na coluna de dados (Payload)!
* **Se entrares num site moderno com HTTPS (porta 443):** Graças à encriptação (TLS), o Wireshark só consegue ver caracteres barulhentos e indifereciados (lixo cifrado). O inspetor postal já não consegue abrir a carta porque ela vai dentro de um cofre blindado!
---

## 🧪 Mestre do Wireshark

### **Perguntas:**
1. Qual é a principal função do Wireshark numa rede de computadores?
* [ ] A) Aumentar a largura de banda e a velocidade do Wi-Fi de casa.
* [ ] B) Capturar e analisar detalhadamente o tráfego de pacotes de rede para fins de diagnóstico e estudo.
* [ ] C) Bloquear automaticamente vírus e ataques de hackers.

---
2. Se quiseres ver apenas os pacotes relacionados com o protocolo DNS no meio de milhares de linhas no Wireshark, o que deves fazer?
* [ ] A) Usar a barra de filtros na parte superior e escrever `dns`.
* [ ] B) Desligar o cabo de rede e voltar a ligar.
* [ ] C) Comprar uma placa de rede com mais velocidade.

## Download: https://www.wireshark.org/download.html
