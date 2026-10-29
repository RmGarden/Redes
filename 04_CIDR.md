# 🔢 O Idioma Secreto dos Computadores
## Binário, Máscaras e o Segredo do CIDR

Para perceberes a 100% porque é que uma máscara de sub-rede é `255.255.255.0` ou porque é que se escreve `/24`, tens de descer ao nível mais básico  do computador: **o sistema binário (os zeros e os uns)**.   
  
Não te preocupes, não precisas de ser um génio da matemática!  
  
---
  
## 💡A Fila de Interruptores de Luz

Os computadores não sabem ler letras nem contar até 10 como nós. No fundo, eles são feitos de milhões de pequenos transístores que só sabem duas  coisas: **LIGADO (1)** ou **DESLIGADO (0)**.  
  
Imagina que tens uma fila de **8 interruptores de luz** (a isto chamamos um *Byte* ou um *Octeto* num endereço IP). Cada interruptor tem um valor   associado, que dobra sempre que vais para a esquerda:  
  
```text
  [ 128 ]  [ 64 ]  [ 32 ]  [ 16 ]  [ 8 ]  [ 4 ]  [ 2 ]  [ 1 ]
```
Para escrevermos um número, basta ligarmos (1) os interruptores cuja soma dê esse número!  
  
Como acender o número 192?  
Se quiseres fazer o número 192 (que aparece tantas vezes nos IPs caseiros), olhas para os interruptores e ligas os que somados dão 192:  
  
128 + 64 = 192 (Os outros ficam a zeros).  
  
Em binário, o 192 fica assim: 11000000  
  
E o número 255 (o máximo num bloco de IP)?  
Para teres o valor máximo, ligas todos os interruptores:  
  
128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255  
  
Em binário, o 255 fica assim: 11111111 (8 uns seguidos)  
  
## 🎭 O Binário e a Máscara de Sub-rede  
Lembras-te da máscara de sub-rede 255.255.255.0?  
Se traduzirmos cada bloco para o seu código binário de interruptores, olhas para isto:  

<pre><code>  255       .   255       .   255       .   0
11111111    . 11111111    . 11111111    . 00000000</code></pre>

Olha bem para o padrão:  
  
Do lado esquerdo, tens uma parede sólida de 1 (tudo ligado). Isto significa: "Aqui os bits são da Rede (a rua)!"  
  
Do lado direito, tens uma parede de 0 (tudo desligado). Isto significa: "Aqui os bits são do Host (a casa)!"  
  
As máscaras de sub-rede servem exatamente para isto: cortam matematicamente a linha entre a Rede e o Dispositivo.  
  
## 🎯 O Segredo do CIDR   
Porque é que se chama /24?    
Agora o mistério do /24 fica resolvido num segundo!    
    
Se contares o número total de 1 (interruptores ligados) na máscara de sub-rede 255.255.255.0:   
  
O primeiro 255 tem 8 uns (11111111)  
  
O segundo 255 tem mais 8 uns (11111111)  
  
O terceiro 255 tem mais 8 uns (11111111)  
  
O 0 tem zero uns (00000000)  
  
Se somarmos todos os 1: 8 + 8 + 8 = 24.  
  
A notação /24 é apenas uma forma preguiçosa de dizer: "A minha máscara tem 24 bits a 1 no início!"  
  
Se a máscara fosse 255.255.0.0, terias 8 + 8 uns, logo seria /16.   
  
## 🧪 Quiz: Mestre do Binário  
  
**Perguntas:**   
  
1. O número 0 em binário, considerando um bloco de 8 interruptores, como se escreve?
    
[ ] A) 11111111  
[ ] B) 00000000  
[ ] C) 10101010  
    

      
3. O que significa uma máscara de sub-rede com a notação /8 em termos de bits ligados (1)?
  
[ ] A) Que os primeiros 8 bits (o primeiro bloco de 255) identificam a rede.  
[ ] B) Que existem 8 computadores na rede.  
[ ] C) Que a velocidade é de 8 Megabits por segundo.  
  

      
4. Porque é que os computadores usam o sistema binário (zeros e uns) em vez do nosso sistema decimal (de 0 a 9)?
  
[ ] A) Porque os engenheiros informáticos achavam graça a essa cor.  
[ ] B) Porque os componentes eletrónicos distinguem facilmente dois estados físicos: corrente elétrica ligada (1) ou desligada (0).  
[ ] C) Porque ocupa mais espaço nos discos rígidos.  
