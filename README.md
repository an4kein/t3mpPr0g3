# t3mpPr0g3

### Author: Eduardo Barbosa (An4kein)

Download software: https://onedrive.live.com/?authkey=%21AOsBPm%2DgVunhDAg&cid=545DAF20AA78D6D3&id=545DAF20AA78D6D3%21884968&parId=545DAF20AA78D6D3%21884967&action=locate

Download Immunity Debugger. : https://debugger.immunityinc.com/ID_register.py

Dwonload Windows-Binaries: https://github.com/interference-security/kali-windows-binaries

Download PyCharm for windows 7 32

```
For 32-bit OS you're limited with PyCharm 2018. 2019 requires 64-bit OS.

You can download 2018.3.7 here: https://www.jetbrains.com/pycharm/download/other.html
```

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


### 2 - Controlando o EIP

