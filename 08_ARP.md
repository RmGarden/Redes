# 🔍 O Protocolo ARP: 
## O Detetive que Descobre as Caras (MAC)

O que já sabemos:   
**Endereço IP** (Camada 3) é a morada lógica da casa  
**Endereço MAC** (Camada 2) é a matrícula física única da placa de rede.  
  
Mas há um grande mistério:  
**Como é que o teu computador descobre o MAC de destino se só sabe o IP?**  

É aqui que entra o **ARP (Address Resolution Protocol)**!

---

## 📢 A Chamada no Salão Cheio de Gente

Imagina que estás numa sala de conferências cheia de pessoas.  
Sabes perfeitamente que o teu colega se chama **João (o IP)**, mas não conheces a cara dele nem tens o cartão de cidadão dele na mão (**o MAC**).

O que fazes? Gritas para a sala toda:
> *"Quem tem o IP 192.168.1.50? Diz-me o teu MAC por favor!"*

Todas as pessoas na sala ouvem (isto é um *Broadcast* na rede local).  
Só uma pessoa, aquela que tem exatamente esse IP é que levanta a mão e responde diretamente:
> *"Sou eu! O meu endereço MAC é `A1:B2:C3:D4:E5:F6`."*

O teu computador guarda essa resposta numa caderneta secreta chamada **Tabela ARP**, para não ter de gritar outra vez da próxima vez que quiser falar com o João.

---

## ⚙️ Como Funciona Passo a Passo?

Quando o teu computador quer enviar um pacote na rede local, ele faz duas perguntas a si mesmo:
1. **O IP de destino está na minha rede local?**
2. Se sim, ele olha para a **Tabela ARP** local:
   * Se já lá estiver o MAC guardado, o pacote é enviado.
   * Se **não estiver**, o computador envia um **ARP Request** (um grito geral para a rede a perguntar *"Quem tem este IP?"*).
   * O dono do IP responde com um **ARP Reply** (*"Sou eu, o meu MAC é este"*).
   * O remetente guarda o par `IP -> MAC` na cache e envia os dados.

---

## 🧪 Quiz: O Inspetor ARP

### **Perguntas:**
1: O que é um pedido ARP (*ARP Request*) na rede local?
* [ ] A) Um email enviado para o servidor de DNS.
* [ ] B) Uma mensagem de *Broadcast* enviada para todos os dispositivos da rede a perguntar quem tem determinado IP.
* [ ] C) Um comando para desligar a placa de rede.

---

2: Para que serve a Tabela ARP armazenada no teu computador?
* [ ] A) Para guardar a lista de correspondências entre endereços IP e endereços MAC recentemente utilizados.
* [ ] B) Para guardar as passwords de todas as redes Wi-Fi a que já te ligaste.
* [ ] C) Para listar as páginas web que visitaste no browser.
