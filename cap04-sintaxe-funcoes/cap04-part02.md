Guardas, guardas!
=================

Enquanto patterns é um jeito de ter certeza de que um valor tenha a forma desejada e torna possível seu desmembramento, guards (guardas) são uma forma de testar se uma (ou mais) propriedades são verdadeiras ou falsas. Se isso te parece muito com um if, está no caminho certo. A diferença é de guards serem mais fáceis de ler em caso de muitas condições além de funcionar com patterns.

Ao invés de parar para explicar a sintaxe, vamos direto criar uma função usando guards. Faremos uma função simples que repreende o usuário de uma forma específica, dependendo do seu <a href="http://pt.wikipedia.org/wiki/%C3%8Dndice_de_massa_corporal"><acronym title="Índice de massa corporal">IMC</acronym></a>. Seu <acronym title="Índice de massa corporal">IMC</acronym> é igual à sua massa dividida pelo quadrado de sua altura. Se seu <acronym title="Índice de massa corporal">IMC</acronym>  está abaixo de 18,5, você é considerado magro. Se está entre 18,5 e 25, é saudável. Entre 25 e 30, acima do peso. Maior, obeso. Então, esta é a função (ela não calcula, somente mostra a mensagem)


Guards são sinalizados por pipes, seguidos do nome de uma função e seus parâmetros. Geralmente, são alinhados e identados à direita. Um guard geralmente é uma expressão booleana. Se for [code]True[/code], a função correspondente é executada. Se [code]False[/code], o resto da linha não é executada e é passado para a próxima. Se chamarmos essa função com [code]24.3[/code], será testado se é menor ou igual a [code]18.5[/code]. Já que não é, o próximo guard é testado. A verificação obtém sucesso ao passar pelo segundo guard, já que 24,3 é menor que 25,0. Assim, é retornado o resultado do segundo guard.

Os guards são remanescentes das árvores encadeadas de if/else da linguagens imperativas, mas muito mais legíveis. Apesar de árvores if/else serem extremamente desaconselhadas, às vezes um problema é definido de um modo que não há muitas alternativas. Em Haskell, Guards são uma solução.

Em vários casos, o último guard é [code]otherwise[/code]. [code]otherwise[/code] é definido com [code]otherwise = True[/code] e aprova tudo. É muito parecido com patterns, que testam por padrões ao invés de condições booleanas. Se todos os guards de uma função derem [code]False[/code] (e não tivermos especificado um guard [code]otherwise[/code]), é testado o próximo <em>pattern</em>. É assim que patterns e guards funcionam bem em conjunto. Se nenhum guard ou pattern se aplicar, é lançado um erro.

E é claro que podemos usar guards com funções que recebam quantos parâmetros desejarmos. Ao invés de obrigarmos o usuário a calcular o seu próprio <a href="http://pt.wikipedia.org/wiki/%C3%8Dndice_de_massa_corporal"><acronym title="Índice de massa corporal">IMC</acronym></a> antes de usar a função, vamos modificá-la para receber altura e peso e descobrir automaticamnte.



Vamos descobrir se eu estou gordo...



Ei! Não estou gordo! Mas Haskell me chamou de feio mesmo assim. Que seja.

Veja que não há um [code]=[/code] depois do nome da função e seus parâmetros, mas antes do primeiro guard. Muitos iniciantes recebem erros de sintaxe ao colocarem aí.

Mais uma outra bem simples: vamos implementar nosso próprio [code]max[/code]. Se não lembra, ele recebe dois parâmetros e retorna o maior.

Guards também podem ser escritos em apenas uma linha, no entanto eu não recomendo graças a sua pouca legibilidade, mesmo em funções curtas. Mas para fins de demonstração, poderíamos escrever nosso [code]max'[/code] assim:


Ugh! Nem um pouco legível! Próximo: nossa própria imprementação de [code]compare[/code] usando guards.



Nota: Do mesmo modo que podemos chamar funções infixas usando crases em volta do seu nome, podemos defini-las. Às vezes se torna mais fácil de ler.
