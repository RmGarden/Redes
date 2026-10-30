# 🏢 VLANs (Virtual Local Area Networks) 
## As Paredes Invisíveis no Escritório

Imagina um grande edifício de escritórios em *open-space* onde trabalham vários departamentos diferentes:  
A **Contabilidade**, os **Recursos Humanos** e os **Convidados do Wi-Fi**.  
  
Se todos estiverem ligados ao mesmo *switch* físico, qualquer pessoa consegue ver o tráfego dos outros.  
Mas será seguro misturar a contabilidade com os convidados? 

A resposta é **não!** É aqui que entram as **VLANs**.

---

## 🧱 As Paredes de Vidro Acústicas

Pensa num andar de um prédio cheio de secretárias:  
**Rede Física Tradicional:**  
Todos os computadores estão ligados por cabos ao mesmo *switch* central.  
É como uma sala aberta onde toda a gente ouve os gritos e conversas uns dos outros.  
  
**VLAN (Virtual LAN):**  
Em vez de gastarmos dinheiro a comprar interruptores e cabos separados para cada departamento, nós construímos **paredes de vidro invisíveis** à volta de cada grupo.  
* As pessoas da Contabilidade continuam fisicamente no mesmo sítio, ligadas ao mesmo aparelho físico, mas o equipamento cria caminhos lógicos separados.
* Os dados da Contabilidade nunca "ouvem" nem entram no mundo dos Convidados!

---

## ⚙️ Como Funcionam as VLANs na Prática?

Para separar o tráfego no mesmo cabo ou *switch*, os equipamentos utilizam uma técnica chamada **Tagging (Etiquetagem)** baseada na norma IEEE 802.1Q:
1. **Portas de Acesso (Access Ports):**
   Ligam-se aos computadores normais.
   O *switch* coloca uma etiqueta invisível (ex: VLAN 10) em todos os pacotes que aquele computador envia.
3. **Portas de Tronco (Trunk Ports):**  
   São os cabos que ligam vários *switchs* entre si.
   Por aqui passam pacotes com etiquetas de **várias VLANs diferentes** misturadas, mas o *switch* do outro lado sabe exatamente para onde direcionar cada pacote com base na sua etiqueta.


# 🧮 Exemplos: 

Já percebemos o que são endereços IP e como funcionam as redes, mas como é que se divide uma rede grande em partes mais pequenas (sub-redes)?  
E como é que os computadores sabem quem pertence ao mesmo "bairro"?

Vamos arregaçar as mangas e fazer contas simples!

---

## 🏫 O Exemplo da Escola: Dividir a Rede em Sub-redes

Imagina que um escola recebeu um bloco de endereços IP da operadora e tens de os dividir para três departamentos diferentes:
* **Administração:** Precisa de no máximo 50 computadores.
* **Alunos (Wi-Fi):** Precisa de no máximo 100 dispositivos.
* **Professores:** Precisa de no máximo 20 computadores.

Como é que o administrador de rede decide a máscara e os limites de cada sub-rede sem gastar IPs à toa?

---

## ⚙️ A Regra de Ouro dos Bits e das Potências de 2

Para calcular sub-redes, lembrate sempre da tabela de potências de 2:
* 2^1 = 2 IPs
* 2^2 = 4 IPs
* 2^3 = 8 IPs
* 2^4 = 16 IPs
* 2^5 = 32 IPs
* 2^6 = 64 IPs
* 2^7 = 128 IPs
* 2^8 = 256 IPs

*(Nota: Deves sempre subtrair **2** ao total de IPs de cada bloco, porque o primeiro IP é o **Endereço de Rede** e o último é o **Broadcast** — esses não podem ser atribuídos a computadores!)*

---

## 📝 Passo a Passo: Criar a Sub-rede para os Alunos (100 dispositivos)

1. **Identificar a necessidade:**
   Precisamos de espaço para 100 computadores de alunos.
  
3. **Escolher o bloco ideal:**
   Olhando para as potências de 2:
   * 2^6 = 64$ (não chega, faltam IPs).
   * 2^7 = 128$ (chega perfeitamente para 128 - 2 = **126 IPs utilizáveis**). Precisamos de **7 bits** para os hosts.
  
5. **Calcular a Máscara de Sub-rede:** 
   * Um endereço IPv4 tem 32 bits no total. Se 7 bits são para os computadores (hosts), sobram 32 - 7 = 25 bits para a rede.
   * Em formato CIDR, esta rede escreve-se: **`/25`**.
   * A máscara em formato decimal fica: `255.255.255.128`.

---

## 🧪 Quiz: Desafio de Sub-redes

### **Perguntas:**
1: Se um computador tem o endereço IP `192.168.1.45` com a máscara de sub-rede `255.255.255.0` (que corresponde a um `/24`), quantos endereços IP utilizáveis é que esta rede disponibiliza para ligar máquinas?
* [ ] A) 256 IPs
* [ ] B) 254 IPs
* [ ] C) 512 IPs

---

2: Porque é que temos de subtrair sempre 2 endereços em cada sub-rede calculada?
* [ ] A) Porque o primeiro IP serve para identificar a rede e o último serve para enviar mensagens de Broadcast para todos.
* [ ] B) Porque os routers antigos estragavam-se se usássemos o primeiro e o último IP.
* [ ] C) É apenas uma lenda urbana da informática, podes usar todos os IPs.

---

3: Qual é a principal vantagem de utilizar VLANs numa rede empresarial?
* [ ] A) Aumentar o comprimento máximo dos cabos de cobre para mais de 5 quilómetros.
* [ ] B) Segmentar uma rede física em várias redes lógicas isoladas, melhorando a segurança e a organização do tráfego.
* [ ] C) Substituir completamente a necessidade de utilizar endereços IP.

---

4: O que é uma porta de *Trunk* (Porta de Tronco) num *switch* de rede?
* [ ] A) A porta onde se liga a impressora de rede.
* [ ] B) Uma porta configurada para transportar tráfego de várias VLANs diferentes entre diferentes *switchs*.
* [ ] C) A porta de alimentação de energia do router.
