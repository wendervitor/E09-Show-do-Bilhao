# PHP: O Show do Bilhão

Nesta série de exercícios iremos praticar o uso da linguagem PHP desenvolvendo uma aplicação web de perguntas e respostas denominado *Show do Bilhão*.

O Show do Bilhão é um programa idealizado pela emissora SBT (Sistema Belo-Horizontino de Televisão). Neste programa, um candidato escolhido da audiência é submetido a uma sequência de 5 perguntas de conhecimento geral. A medida em que o candidato responde cada pergunta ele avança no jogo. 

O jogo termina quando o candidato responde uma pergunta incorretamente. Após o término do jogo o sistema calcula a pontuação final do candidato. Sua pontuação é dada pela quantidade de perguntas respondidas corretamente pelo candidato.

O proprietário da emissora requisitou que você desenvolvesse uma aplicação web que gerencie as perguntas do jogo. Mais especificamente, esse sistema irá fazer o controle das respostas do jogo


## Introdução: Prova de Conceito

O primeiro passo é elaborar uma prova de conceito para mostrar ao conselho diretor. Implemente uma página em PHP que carregue e exiba as perguntas (Todas na mesma página).

Segue alguns requisitos:
* Você deverá utilizar arrays para armazenar os dados das perguntas:
    * um vetor para enunciados
    * uma matriz (vetor de vetores) com as alternativas
    * um vetor com o índice para a alternativa certa
* Deverá haver um loop que irá iteragir com cada pergunta para carregá-la e exibi-la na página

## Separando uma pergunta por página

Agora que a prova de conceito foi implementada, você deverá separar as perguntas de forma a exibir uma por página. Para poder definir qual pergunta será exibida, a página receberá como parâmetro de uma requisição do tipo `GET` o índice de acesso da pergunta que será exibida. Por exemplo, uma requisição para `http://localhost:8080/perguntas.php?id=3` irá carregar na página `perguntas.php` a pergunta armazenada na posição 3 do vetor.

Segue alguns requisitos:
* A pergunta deverá ser recuperada através de uma função chamada `carregaPergunta($id)` que irá acessar o vetor de perguntas, alternativas e respostas, e retornar os dados referentes a pergunta selecionada.
* A função implementada anteriormente deverá ser armazenada em um partial chamado `perguntas.inc`. Esse partial conterá funções auxiliares que irão manipular as perguntas da página. É importante ressaltar que esse conjunto de funções é fundamental para o funcionamento do sistema.
* A sua página conterá alguns trechos em HTML que poderão ser reaproveitados em outros momentos, como menu, rodapé, etc. Crie dois arquivos, chamados `menu.inc` e `rodape.inc` que irão armazenar o código HTML do menu e rodapé, e importe-os na página de perguntas. Diferentemente do arquivo `perguntas.inc`, o sistema pode tolerar eventuais problemas de carregamento do menu e rodapé.

## Checando respostas

Agora que as perguntas foram separadas por página. Você deverá implementar a lógica de evolução do jogo. Ao entrar na página inicial do jogo, a primeira pergunta deverá ser carregada. O usuário então seleciona a alternativa que ele julgar correta e submete a resposta. O sistema deverá verificar a resposta do usuário. Caso a resposta esteja correta, o usuário avança para a próxima pergunta. Caso contrário ele deverá ser redirecionado para uma página de game over.

Segue alguns requisitos:
* As alternativas para as perguntas deverão ser fornecidas por meio de um formulário, para possibilitar o envio da resposta ao servidor
* Seu sistema deverá exibir um progresso do jogo (Quantas perguntas ele acertou, por exemplo).
* Os dados deverão ser enviados através de requisições do tipo `POST`.

*dica: você precisará enviar entre as requisições um identificador de qual pergunta será mostrada ao usuário. Pesquise sobre __hidden input fields__.*

## Identificando o jogador

Chegou a hora de seu programa identificar o jogador que está participando do jogo. Utilize os conceitos de sessões e cookies para identificar quem está jogando. O jogador que está jogando no momento deverá ser identificado por meio de sessão. Utilize cookies para mostrar ao usuário quando foi a última vez que ele jogou e qual foi sua última pontuação.

Segue alguns requisitos:
* O jogador não poderá acessar as perguntas se ele não tiver sido identificado antes. Ou seja, você precisará implementar um simples método de autenticação.
* Deverá haver uma opção para que o jogador se desidentifique do jogo para que outro possa jogar. Ou seja, você precisará implementar uma rotina de logout.

