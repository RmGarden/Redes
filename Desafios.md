# 🧩 Desafios Práticos de Redes

Estás pronto para testar o que aprendeste na prática? 
Tenta resolver cada desafio sozinho antes de espreitar as soluções no fundo da página!

---

## 📦 Desafio 1: A Viagem do Pacote (Modelo OSI na Prática)  
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

---
## 🧮 Desafio 2: O Arquiteto de Sub-redes (IP & CIDR)
**Cenário:**  
Foste contratado para organizar a rede de uma pequena startup com 30 computadores no escritório principal.  
  
**Tarefa:**  
O teu chefe deu-te uma rede com o endereço base 192.168.1.0.   
Nota: Precisas de acomodar pelo menos 30 dispositivos mais o gateway e o endereço de rede    
  
**Pergunta:**  
1: Qual é a máscara de sub-rede em formato CIDR (ex: /24, /26, /27) que deves escolher para não desperdiçar demasiados endereços IP?  
2: Quantos endereços IP utilizáveis é que essa sub-rede te vai dar?  

---
## 🔍 Desafio 3: O Guia Telefónico da Internet (DNS)

**Cenário:**   
Sempre que escreves `github.com` no teu browser, o computador não faz ideia de onde fica esse nome.  
Ele precisa do endereço IP real. É aqui que entra o **DNS (Domain Name System)**.

**Tarefa:**  
Abre a linha de comandos.
Usa a ferramenta de consulta de DNS escrevendo: nslookup github.com  
  
**Pergunta:**
1. Qual é o endereço IP que o servidor DNS devolveu para o site do GitHub?
2. Em que porta padrão da Camada de Transporte costuma operar o serviço DNS?

--- 
## ⚡ Desafio 4: O Distribuidor Automático (DHCP)  
**Cenário:**  
Ligaste o teu portátil ao Wi-Fi e, num segundo, tens um IP atribuído sem precisares de configurar nada à mão.   
Quem fez a magia nos bastidores foi o DHCP (Dynamic Host Configuration Protocol).  
  
**Tarefa:**  
Na tua linha de comandos, escreve o comando para ver a tua configuração de rede atual:  

No Windows: ipconfig /all  
No Mac/Linux: ifconfig ou ip a  

**Pergunta:**  
1. Consegues identificar qual é o endereço IP do teu Gateway Padrão (Default Gateway)?
2. O endereço IP que o teu PC recebeu é definitivo ou tem um Lease Time (tempo de empréstimo)?

---
## 🚪 Desafio 5: O Porteiro das Portas (TCP/UDP Ports)
**Cenário:**  
O teu computador tem um único endereço IP,  
mas consegues correr o Spotify, abrir 10 separadores no Chrome e estar numa chamada de voz no Discord ao mesmo tempo,  
sem que os pacotes de dados se misturem.   
  
Como é que isto é possível? Graças às Portas!  
  
**Tarefa:**  
Pensa nos serviços que usas diariamente e identifica:  
  
**Perguntas**   
1: Qual é a porta padrão usada para páginas web encriptadas e seguras (HTTPS)?  
2: Qual é a porta padrão usada para envio de emails (SMTP)?  
  
---
## Soluções  

### Solução do Desafio 1 (Modelo OSI)  
Resposta:  
1. O comando ping usa o protocolo ICMP, gerido na Camada 3 (Rede).  
2. O endereço 8.8.8.8 é um endereço IP, operando também na Camada 3 (Rede).  
  
### Solução do Desafio 2 (Subnetting)  
1: Deves usar a máscara /27 (que equivale a 255.255.255.224).  
2: Uma máscara /27 dá um total de 32 endereços por sub-rede. Como 1 é para a rede e 1 é para o broadcast, ficam disponíveis 30 endereços IP   utilizáveis para os computadores da startup.  

### Solução do Desafio 4 (DNS)  
1: O nslookup devolve os endereços IP (IPv4 e/ou IPv6) associados aos servidores do GitHub.  
2: O DNS opera na Porta 53 (usando UDP para consultas rápidas e TCP para transferências maiores).  

### Solução do Desafio 5 (DHCP)  
1: O Default Gateway é o IP do router que encaminha o teu tráfego para fora da rede local (normalmente termina em .1, como 192.168.1.1).  
2: Os IPs do DHCP são temporários (Lease Time). Quando o tempo expira, o dispositivo pede renovação da morada.  
   
### Solução do Desafio 6 (Portas)  
1: O HTTPS utiliza sempre a Porta 443 (o HTTP antigo usava a porta 80).  
2: O protocolo SMTP (para enviar correio eletrónico) utiliza a Porta 25 (ou 587 para conexões seguras).  
