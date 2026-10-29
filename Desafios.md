# 🧩 Desafios Práticos de Redes

Estás pronto para testar o que aprendeste na prática? 
Tenta resolver cada desafio sozinho antes de espreitar as soluções no fundo da página!

---

📦 Desafio 1: A Viagem do Pacote (Modelo OSI na Prática)
**Cenário:** 
Queres enviar uma mensagem no Discord para um colega. 
O teu computador tem de encapsular a mensagem através das 7 camadas do Modelo OSI.

**Tarefa:**
Abre a linha de comandos.
Escreve o comando para testar a ligação a um servidor conhecido (por exemplo, o Google):

ping 8.8.8.8

**Pergunta:**
1. Qual foi a camada do Modelo OSI que gerou o comando ping?
2. Em que camada opera o endereço 8.8.8.8 que aparece no ecrã?


🧮 Desafio 2: O Arquiteto de Sub-redes (IP & CIDR)
**Cenário:** 
Foste contratado para organizar a rede de uma pequena startup com 30 computadores no escritório principal.

**Tarefa:**
O teu chefe deu-te uma rede com o endereço base 192.168.1.0. 
Sabendo que precisas de acomodar pelo menos 30 dispositivos mais o gateway e o endereço de rede:

**Pergunta:** 
1: Qual é a máscara de sub-rede em formato CIDR (ex: /24, /26, /27) que deves escolher para não desperdiçar demasiados endereços IP?
2: Quantos endereços IP utilizáveis é que essa sub-rede te vai dar?




Solução do Desafio 1 (Modelo OSI)
Resposta:
1. O comando ping usa o protocolo ICMP, gerido na Camada 3 (Rede).
2. O endereço 8.8.8.8 é um endereço IP, operando também na Camada 3 (Rede).

Solução do Desafio 2 (Subnetting)
1: Deves usar a máscara /27 (que equivale a 255.255.255.224).
2: Uma máscara /27 dá um total de 32 endereços por sub-rede. Como 1 é para a rede e 1 é para o broadcast, ficam disponíveis 30 endereços IP utilizáveis para os computadores da startup.
