# 🌍 O Processo DNS  
## A Lista Telefónica da Internet

Sempre que escreves `github.com` ou `google.com` no teu browser, tu não sabes de cor o endereço IP numérico daquele servidor.  
É aqui que entra o **DNS (Domain Name System)**, o sistema que traduz nomes legíveis para humanos em endereços IP compreensíveis pelos computadores.  
  
Mas como é que este processo acontece em frações de segundo nos bastidores? Vamos descobrir!  
  
---
  
## 📞 Encontrar um Amigo numa Lista Global

Imagina que queres ligar para uma pessoa famosa, mas só sabes o nome artístico dela. 
1. **O teu telemóvel (Cache Local):**
   Primeiro, olhas para a tua agenda recente para ver se já ligaste a essa pessoa antes. Se sim, ligas de imediato.

4. **O Balcão de Informações do Bairro (DNS Resolver / ISP):**
 Se não tens o número, perguntas ao rececionista da tua zona (o servidor DNS da tua operadora de internet ou o `8.8.8.8` da Google).
*"Sabes o número de telefone de github.com?"*

7. **O Diretor de Servidores Raiz (Root Servers):**
 Se o rececionista do bairro não sabe, ele bate à porta do "Diretor Geral" da lista telefónica mundial, que diz:
*"Não sei o número exato, mas sei quem cuida de todas as páginas terminadas em `.com`!"*

9. **O Servidor do TLD (`.com`):**  
 Esse servidor especializado diz: *"Também não sei a morada completa, mas o servidor oficial responsável pelo domínio `github.com` é aquele ali em baixo."*

11. **O Servidor Autoritativo:** Finalmente, chegas ao servidor oficial do próprio GitHub, que te dá o IP exato: `140.82.114.3`.  
O teu computador guarda essa informação numa caderneta (cache) e estabelece a ligação de imediato!  

---

## ⚙️ Os 4 Passos da Consulta DNS

Quando o teu sistema operativo faz um pedido DNS (*DNS Query*), o fluxo segue esta ordem estrita:
1. **Recursive Resolver:** Recebe o teu pedido e faz o trabalho de investigação por ti.
2. **Root Name Servers (`.`):** O topo da árvore DNS mundial.
3. **TLD Name Servers (`.com`, `.pt`, `.org`):** Guardam os apontamentos das extensões de topo.
4. **Authoritative Name Servers:** O servidor final gerido pela empresa dona do domínio, que tem a resposta final e oficial com o IP.

---

## 🧪 Quiz: Mestre do DNS

### **Perguntas:**
1: O que faz um servidor DNS autoritativo?
* [ ] A) Atribui endereços IP temporários aos telemóveis via DHCP.
* [ ] B) Fornece a resposta oficial e definitiva com o endereço IP associado a um nome de domínio.
* [ ] C) Bloqueia o tráfego de vírus informáticos na rede local.

---

2: O que acontece se o teu computador tentar aceder a um site na Internet e o **DNS Resolver** falhar ou estiver inacessível?
* [ ] A) Consegues aceder a recursos locais por IP, mas o browser não consegue traduzir nenhum nome de site (dando erro de DNS).
* [ ] B) O teclado deixa de funcionar.
* [ ] C) O endereço IP do teu computador muda automaticamente para IPv6.
