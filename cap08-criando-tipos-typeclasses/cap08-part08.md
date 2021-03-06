Uma typeclass sim-não
=====================

Em JavaScript e outras linguagens fracamente tipadas, você pode pôr quase qualquer coisa dentro de uma expressão. Por exemplo, você pode fazer tudo o que se segue: [code]if (0) alert("YEAH!") else alert("NO!")[/code], [code]if ("") alert ("YEAH!") else alert("NO!")[/code], [code]if (false) alert("YEAH") else alert("NO!)[/code], etc. e todos esses vão mandar um alerta de [code]NO![/code]. Se você fizer [code]if ("WHAT") alert ("YEAH") else alert("NO!")[/code], vai alertar um [code]"YEAH!"[/code] porque JavaScript considera palavras não vazias como tendo um valor meio verdadeiro.

Mesmo que o uso estrito de [code]Bool[/code] para semânticas booleanas funcione melhor em Haskell, vamos tentar implementar aquele comportamento meio JavaScript. Por diversão! Vamos começar com uma declaração <i>class</i>.


Muito simples. A typeclass [code]YesNo[/code] define uma função. Tal função pega um valor de um tipo que é considerado conter algum valor de verdade e nos diz com certeza se é verdadeiro ou não. Note que da forma como utilizamos [code]a[/code] na função, [code]a[/code] tem que ser um tipo concreto.

Agora, vamos definir algumas instâncias. Para números, vamos assumir que (como em JavaScript) qualquer número que não seja 0 é verdadeiro e 0 é falso.



Listas vazias (e por extensão, strings) são valores negativos, enquanto que listas não-vazias são valores verdadeiros.



Note como acabamos de pôr um parâmetro de tipo [code]a[/code] lá para tornar a lista um tipo concreto, mesmo que não façamos nenhuma suposição sobre o tipo que está contido na lista. O que mais, hmm... já sei, o próprio [code]Bool[/code] guarda verdade e falsidade, e é bem óbvio qual é qual.

Han? O que é [code]id[/code]? É apenas uma função padrão da biblioteca que pega um parâmetro e retorna a mesma coisa, que é o que estaríamos escrevendo de qualquer forma.

Vamos tornar [code]Maybe a[/code] uma instância também.



Nós não precisamos de uma restrição de classe porque não fizemos nenhuma suposição sobre o conteúdo de [code]Maybe[/code]. Apenas dissemos que é verdadeiro se for um valor [code]Just[/code] e falso se for um [code]Nothing[/code]. Ainda tivemos de escrever [code](Maybe a)[/code] ao invés de apenas [code]Maybe[/code] porque, se você parar pra pensar, uma função [code]Maybe -&gt; Bool[/code] não pode existir (porque [code]Maybe[/code] não é um tipo concreto), onde que [code]Maybe a -&gt; Bool[/code] está bem e elegante. Ainda sim, isso é muito legal porque, agora, qualquer tipo na forma [code]Maybe something[/code] é parte de [code]YesNo[/code] e não importa o que [code]something[/code] é.

Anteriormente, definimos um tipo[code]Tree a[/code], que representava uma árvore de busca binária. Podemos dizer que uma árvore vazia é falsa e qualquer coisa que não seja vazia seja verdadeira.



Um semáforo pode ter um valor de sim ou não? Certamente. Se for vermelho, você para. Se for verde, você vai. Se for amarelo? Eh, eu geralmente ultrapasso amarelos porque eu vivo para a adrenalina.


Legal, agora que temos algumas instâncias, vamos brincar!



Certo, funciona! Vamos fazer uma função que imita o if, mas funciona com valores [code]YesNo[/code].


Bem direto ao ponto. Precisa de um valor sim-ou-não e duas coisas. Se o valor s-m-ou-não for mais pra um sim, retorna a primeira das duas coisas, caso contário, retorna a segunda delas.