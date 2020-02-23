# t3mpPr0g3

### Author: Eduardo Barbosa (An4kein)

Download software: https://onedrive.live.com/?authkey=%21AOsBPm%2DgVunhDAg&cid=545DAF20AA78D6D3&id=545DAF20AA78D6D3%21884968&parId=545DAF20AA78D6D3%21884967&action=locate

Download Immunity Debugger. : https://debugger.immunityinc.com/ID_register.py

Dwonload Windows-Binaries: https://github.com/interference-security/kali-windows-binaries

### 1 - Interagindo com o axp202001

Primeiro tentei entender como funciona o programa, logo observei quando abri o mesmo com o Immunnity Debugger que ele abria a porta 4321.

![initi_port](https://raw.githubusercontent.com/an4kein/t3mpPr0g3/master/images/init_port.png)

tambem pode ser passado qualquer outra porta, isso fica a seu criterio...

![otherport](https://raw.githubusercontent.com/an4kein/t3mpPr0g3/master/images/other_port.png)

Uma outra maneira era fazer um fuzer de portas, ate encontrar a porta na qual ele abre.

Continuando...

Inicialmente enviei um (A) e o programa me retornava (COMPLETE), mandei outras informacoes de teste, sempre aumentando a quantidade de caracteres enviado.

![interagindo](https://raw.githubusercontent.com/an4kein/t3mpPr0g3/master/images/2-interagindo.png)

Precisamos analisar melhor, nesse momento entrar o famoso (Immunity Debugger) atraves dele vamos debugar com mais detalhes, pois comecaremos agora o fuzzer, ate encontrar o momento em que o "PROGRAMA CRASHA"

Abre seu Immunity Debugger em seguida abra o axp202001 e de play nele.

![open_prog](https://raw.githubusercontent.com/an4kein/t3mpPr0g3/master/images/3-openprog.png)

Observe que ele encontra-se pausado, precisamos dar play.

![play_prog](https://raw.githubusercontent.com/an4kein/t3mpPr0g3/master/images/4-play_prog.png)

Apos dar o play, uma janela eh aberta informando que esta tudo ok e podemos comecar a brincadeira.

![executando](https://raw.githubusercontent.com/an4kein/t3mpPr0g3/master/images/5-executando.png)

Vamos enviar determinadas quantidades de bytes (caracteres) ate o programa crashar, observe que foi estabelecida a conecao.

![connect](https://raw.githubusercontent.com/an4kein/t3mpPr0g3/master/images/6-connect.png)

Interessante que enviei apenas um (A) e o programa ja dava chash, no exemplo a seguir enviei (an4kein). 

![crash_1](https://raw.githubusercontent.com/an4kein/t3mpPr0g3/master/images/7-crash-1.png)

Uma vez um colega meu falou, envia 5000k de bytes inicialmente..... Ahhh, entao vamos fazer isso!!! haha.. Antes eu particulamente fazia o fuzzer, mas neste caso vou dar preferencia e seguir a dica do meu mano.

![crash_2](https://raw.githubusercontent.com/an4kein/t3mpPr0g3/master/images/8-crash-2.png)

Nosso code encontra-se na base inicial de interatividade com o programa

```
import socket
import struct

server = '127.0.0.1'
port = 4321

buf = "A" * 5000
payload = buf
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((server, port))
s.recv(1024)
s.send(payload)
s.close()
```


### 2 - Controlando o EIP

Precisamos encontrar nosso offset, e assim poder escrever nossos B's no  EIP, portanto nao usarei o famoso (pattern_create) default do kali, pois estou usando o Qubes-OS e ainda nao terminei de deixar liso meu kali, pois so estava conseguindo rodar via LiveCD e no entanto preciso salvar varias coisas e isso estava me dando muito trampo, entao hoje resolvi configurar o Kali em cima do debian10, logo nao terminei de configurar como eu quero. 

Entao, vou usar uma plataforma online para gerar meu pattern

LINK: https://zerosum0x0.blogspot.com/2016/11/overflow-exploit-pattern-generator.html

![pattern_online](https://raw.githubusercontent.com/an4kein/t3mpPr0g3/master/images/9-pattern_online.png)
