Title: Calculando datas no Bash
Date: 2021-01-23 13:35
Category: Bash
Tags: bash, data
Slug: calculando-datas-no-bash
Summary: Uma apresentação rápida e clara sobre o cálculo de datas usando o bash

### Introdução
Algumas vezes precisamos fazer alguns cálculos sobre datas para realizar alguma tarefa, quando isso é necessário e temos acesso a um shell bash as coisas ficam bem faceis, abaixo procuro mostrar de maneira rápida e clara como podemos fazer isso.

### Realizando cálculo sobre datas
Para realizarmos cálculos sobre datas no bash, irei utilizar o comando date<sup>1</sup>, a seguir mostro alguns exemplos que considero ajudar aqueles que precisam realizar alguma tarefa envolvendo datas no bash.
* Saber a data atual
```
$ date
Sat 23 Jan 2021 03:30:16 PM -03
```
Para sabermos qual a data daqui a **x** dias, temos que usar o parametro *-d* do comando date e em seguida passar a frase "now *+y/-y* day" (onde +/- informa se queremos saber uma data futura ou passada e y representa a quantidade de dias), por exemplo:
* Saber a data daqui a 7 dias
```
$ date -d "now +7 day"
Sat 30 Jan 2021 03:31:57 PM -03
```
* Saber a data daqui a 30 dias
```
$ date -d "now +30 day" 
Mon 22 Feb 2021 03:32:56 PM -03
```
* Saber a data de 30 dias atrás
```
$ date -d "now -30 day" 
Thu 24 Dec 2020 03:38:26 PM -03
```
Acima utilizamos *days* para fazer o cálculo, mas podemos utilizar outros parâmetros se desejarmos, sendo eles:
* second
* minute
* hour
* day (utilizado nos comandos acima)
* week
* month
* year

Abaixo segue mais exemplos utilizando os outros parâmetros mencionados acima.
* Saber a data daqui a 3 meses
```
$ date -d "now +3 month"
Fri 23 Apr 2021 03:47:49 PM -03
```
* Saber a data de 2 meses atrás
```
$ date -d "now -2 month"
Mon 23 Nov 2020 03:48:37 PM -03
```
* Saber a data daqui a 5 semanas
```
$ date -d "now +5 week"
Sat 27 Feb 2021 03:49:44 PM -03
```
* Saber a data de 1 semana atrás
```
$ date -d "now -1 week"
Sat 16 Jan 2021 03:50:59 PM -03
```
* Saber a data daqui a 7 anos
```
$ date -d "now +7 year"
Sun 23 Jan 2028 03:51:53 PM -03
```
* Saber a data de 10 anos atrás
```
$ date -d "now -10 year"
Sun 23 Jan 2011 04:52:42 PM -02
```
Conforme os exemplos acima, pode ser visto como é fácil saber as datas futuras e passadas utilizando o bash, basicamente é conversar com ele em apenas uma linha e o resultado vem.

### Formatando a saída
Como deve ter sido notado acima, as datas estão vindo no padrão LC_TIME para en_US.UTF-8, porém essa saída pode ser configurada conforme a sua necessidade, basta que você informe ao bash como deseja a formatação, algumas opções disponiveis serão descritas a seguir, a lista completa pode ser conferida em [Date conversion specifiers](https://www.gnu.org/software/coreutils/manual/html_node/Date-conversion-specifiers.html#Date-conversion-specifiers).
* %a = o nome abreviado do dia da semana da localidade (por exemplo, 'Sáb')
* %A = o nome completo do dia da semana da localidade (por exemplo, 'sábado')
* %b = o nome abreviado do mês da (por exemplo, 'Jan')
* %A = o nome completo do mês da localidade (por exemplo, 'janeiro')
* %d = o dia do mês (por exemplo, '01')
* %m = mês ('01'...'12')
* %Y = ano (por exemplo, 2021)

Alguns exemplos do que foi dito acima são:
```
$ date -d "now 2 month" +"%d/%m/%Y"
23/03/2021
```
```
$ date -d "now 10 week" +"%d/%m/%Y"
03/04/2021
```

Caso queira converter a hora, a lista completa pode ser conferida em [Time conversion specifiers](https://www.gnu.org/software/coreutils/manual/html_node/Time-conversion-specifiers.html#Time-conversion-specifiers), algumas opções são:
* %H = hora ('00'...'23')
* %M = minutos ('00'...'59')
* %S = segundos ('00'...'60'). '60' se houver suporte para segundos bissextos.
* %T = Hora, minuto e segundo. Igual a '%H:%M:%S' (Apresentação usando 24 horas).

Alguns exemplos do que foi dito acima são:
```
$ date -d "now +35 days" +"%T"
16:21:48
```
```
$ date -d "now +35 days" +"%H/%M"
16/22
```

### Conclusão
Por hoje o que tenho para mostrar é isso, com um simples comando em bash podemos obter a data desejada usando poucos parâmetros.
Não coloquei exemplos acima, mas os parâmetros para obter a data podem ser combinados, como por exemplo:
```
$ date -d "now +20 day +2 hour +5 month +3 year"
Sat 13 Jul 2024 06:27:39 PM -03
```
```
$ date -d "now -10 day +5 hour +5 month -2 year"
Thu 13 Jun 2019 09:28:27 PM -03
```
