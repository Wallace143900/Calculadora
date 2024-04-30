Sobre a Lógica desse projeto que controla o fluxo de entrada de uma calculadora e executa as operações matemáticas correspondentes, atualizando o visor conforme necessário.

Variáveis Globais:

-runningTotal: Armazena o resultado acumulado das operações.

-buffer: Armazena o valor atual que está sendo exibido na tela da calculadora.

-previousOperator: Armazena o operador (como +, -, ×, ÷) usado na operação anterior.

================================================================

Seleção do Elemento da Tela:

-screen: É uma referência ao elemento HTML que representa a tela da calculadora. Esse elemento é selecionado usando document.querySelector('.screen').

=================================================================

Função buttonClick(value):

-Esta função é chamada quando um botão é clicado na calculadora.

-Ela verifica se o valor clicado é um número ou um símbolo (como um operador ou um comando especial).

-Dependendo do tipo do valor, chama handleSymbol(symbol) ou handleNumber(value).

Em seguida, atualiza o texto exibido na tela da -calculadora com o conteúdo do buffer.

=================================================================

Função handleSymbol(symbol):

-Esta função lida com símbolos (como operadores ou comandos especiais) quando um botão correspondente é clicado.

-Os casos principais são:
'C': Limpa o buffer e o total acumulado.
'=': Realiza a operação pendente com o operador anterior.
'←': Remove o último caractere do buffer.
Operadores (+, -, ×, ÷): Chama a função handleMath(symbol) para lidar com a operação matemática.

=================================================================

Função handleMath(symbol):

-Esta função lida com operações matemáticas (como adição, subtração, multiplicação, divisão) quando um operador é clicado.

-Se o buffer atual for diferente de '0', converte-o em um número inteiro.

-Se runningTotal for zero, atribui o valor do buffer a runningTotal. Caso contrário, chama flushOperator(intBuffer) para realizar a operação pendente.

-Atualiza previousOperator com o operador atual e redefine o buffer para '0'.

=================================================================

Função flushOperator(intBuffer):

-Esta função executa a operação matemática pendente com o operador anterior e o número fornecido.

-Dependendo do operador anterior (+, -, ×, ÷), executa a operação correspondente e atualiza runningTotal.

=================================================================

Função handleNumber(numberString):

-Esta função é chamada quando um número é clicado na calculadora.

-Se o buffer atual for '0', substitui-o pelo número clicado. Caso contrário, concatena o número clicado ao buffer atual.

=================================================================

Função init():

-Esta função é chamada para inicializar a calculadora.
Adiciona um ouvinte de evento de clique aos botões da calculadora para chamar a função buttonClick(value) quando um botão é clicado.