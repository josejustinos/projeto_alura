# projeto_alura
Projeto da Alura - Encontra Concurso
O projeto consiste em fazer a leitura de um EDITAL (arquivo tipo pdf) e encontrar determinado conteúdo.
Pode ser ser usado para encontrar concurso público, vagas, licitação, etc. Claro que com algumas adaptações.
Aqui usaremos para procurar vagas de concursos públicos.
A ideia que eu tive é para automatizar o processo, mas por conta do tempo baixa-se o arquivo de uma cidade qualquer e procura se a mesma possui algum concurso público em aberto.

Descrição do projeto: Um programa onde o usuário faça o input de um arquivo em pdf. Após fazer o carregamento do arquivo pdf, o algorítimo deve fazer uma análise criteriosa no arquivo pdf e procurar pelas frases por exemplo, inscrição para concurso público ou vagas para concurso público no arquivo carregado, se encontrado alguma referêcia a concurso público, procurar as seguintas informações sobre o concurso público, as vagas disponíveis do concurso, o grau de escolaridade para concorrer a vaga do concurso, data inicial e data final de inscrição para o concurso, valor da inscrição para o concurso, local ou site para realizar a inscrição do concurso. Após encontrar essas informações exibir em tela uma em cada linha. 
Após exibir todas as vagas encontradas mostrar duas opções ao usuário, uma para ele encerrar a execução e outra para inserir outro arquivo pdf. Caso ele escolha a opção de encerrar o programa ele será fechado. Caso escolha inserir outro arquivo o prgrama volta na opção para o usuário dar o input de outro arquivo pdf para ser analisado.
Caso não seja encontrado nada referente a concurso público ou vaga de concurso público no arquivo pdf deve ser informado ao usuário que não foram encontradas vagas naquele documento pdf. Após informar que não foram encontradas vagas de concurso mostrar duas opções ao usuário, uma para ele encerrar a execução do programa e outra para inserir outro arquivo pdf. Caso ele escolha a opção de encerrar o programa ele será fechado. Caso escolha inserir outro arquivo o prgrama volta na opção inicial para o usuário dar o input de outro arquivo pdf para ser analisado.

Explicação do código
No arquivo projeto_alura está um exemplo de código em Python para realizar a tarefa descrita. O código utilizará a biblioteca `PyMuPDF` para ler o arquivo PDF e extrair o texto. Em seguida, ele procura por palavras-chave e frases que indicam a presença de informações sobre concurso público e tenta encontrar os detalhes solicitados.
Deve ser ressaltado que a eficácia do código em extrair informações corretas depende da consistência do formato das informações nos arquivos PDF e pode ser necessário ajustar os padrões de pesquisa e a lógica de extração para funcionar com diferentes layouts.
