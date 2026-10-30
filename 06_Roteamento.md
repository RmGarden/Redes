# 🛣️ Roteamento Estático & Default Gateway 
## O GPS da Rede

Imagina que os pacotes de dados são carros a tentar viajar de uma cidade para outra.  
Enquanto estão dentro do mesmo espaço fechado, andam pelas ruas internas.  
Mas quando o destino é fora de portas, precisam obrigatoriamente de passar pela entrada principal. 

É aqui que entram as **Tabelas de Roteamento** e o **Default Gateway (Gateway Padrão)**.
---

## 🧭 O Condomínio Fechado e a Portaria

Pensa no teu computador como um carro a circular dentro de um **condomínio fechado**:

* **Rede Local (LAN):**
  Se queres enviar um ficheiro para o computador do teu irmão que está ligado ao mesmo router Wi-Fi, o pacote viaja diretamente de porta em porta dentro do condomínio, sem precisar de falar com o mundo exterior.
  
* **O Default Gateway (A Portaria / O Router de Casa):**  
  Se queres aceder ao YouTube, o teu computador olha para a morada de destino e percebe:    
  *"Epa, este IP não pertence ao nosso condomínio!"*   
Nesse momento, o computador aplica a regra de ouro:  
  *"Se não sei onde fica, envio tudo para a **portaria principal** — o **Gateway Padrão**."*  
* O router da operadora atua como o **porteiro ou o GPS central**, recebendo o pacote na saída e encaminhando-o de router em router pelas autoestradas globais da Internet até chegar ao servidor certo.  

---

## 📋 Como Funciona a Tabela de Roteamento?

Todos os dispositivos com capacidade de rede (computadores, telemóveis, routers) têm uma **Tabela de Encaminhamento (Routing Table)** guardada na memória. Podes consultá-la facilmente:
* Windows: Escreve `route print` na linha de comandos.
* Linux: Escreve `netstat -rn` ou `ip route`.

Esta tabela funciona como um mapa de estradas que diz ao sistema:
* *"Para ir para a rede `192.168.1.0`, envia diretamente pela placa de rede local."*
* *"Para ir para qualquer outro sitio do planeta (`0.0.0.0/0`), envia obrigatoriamente para o IP do router (`192.168.1.1`)."*

---

## 🧪Quiz: Mestre do Roteamento

### **Perguntas:**  

1: O que é o Default Gateway (Gateway Padrão) numa rede doméstica?
* [ ] A) O servidor que guarda as passwords do Wi-Fi.
* [ ] B) O endereço IP do router que serve como ponto de saída obrigatório para tráfego destinado a outras redes ou à Internet.
* [ ] C) O cabo de rede que liga o computador à tomada da parede.

---

2: O que acontece se o teu computador tentar aceder a um site na Internet e o **Default Gateway** estiver mal configurado ou desligado?
* [ ] A) Consegues falar com os computadores da tua rede local, mas perdes completamente o acesso à Internet externa.
* [ ] B) O teclado deixa de funcionar.
* [ ] C) O endereço IP do teu computador muda automaticamente para IPv6.
