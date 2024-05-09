# projeto_alura
Projeto da Alura - Encontra Concurso
O projeto consiste em fazer a leitura de um EDITAL (arquivo tipo pdf) e encontrar determinado conteúdo.
Pode ser ser usado para encontrar concurso público, vagas, licitação, etc. Claro que com algumas adaptações.
Aqui usaremos para procurar vagas de concursos públicos.
A ideia que eu tive é para automatizar o processo, mas por conta do tempo baixa-se o arquivo de uma cidade qualquer e procura se a mesma possui algum concurso público em aberto.

Descrição do projeto: Um programa onde o usuário faça o input de um arquivo em pdf. Após fazer o carregamento do arquivo pdf, o algorítimo deve fazer uma análise criteriosa no arquivo pdf e procurar pelas frases por exemplo, inscrição para concurso público ou vagas para concurso público no arquivo carregado, se encontrado alguma referêcia a concurso público, procurar as seguintas informações sobre o concurso público, as vagas disponíveis do concurso, o grau de escolaridade para concorrer a vaga do concurso, data inicial e data final de inscrição para o concurso, valor da inscrição para o concurso, local ou site para realizar a inscrição do concurso. Após encontrar essas informações exibir em tela uma em cada linha. 
Após exibir todas as vagas encontradas mostrar duas opções ao usuário, uma para ele encerrar a execução e outra para inserir outro arquivo pdf. Caso ele escolha a opção de encerrar o programa ele será fechado. Caso escolha inserir outro arquivo o prgrama volta na opção para o usuário dar o input de outro arquivo pdf para ser analisado.
Caso não seja encontrado nada referente a concurso público ou vaga de concurso público no arquivo pdf deve ser informado ao usuário que não foram encontradas vagas naquele documento pdf. Após informar que não foram encontradas vagas de concurso mostrar duas opções ao usuário, uma para ele encerrar a execução do programa e outra para inserir outro arquivo pdf. Caso ele escolha a opção de encerrar o programa ele será fechado. Caso escolha inserir outro arquivo o prgrama volta na opção inicial para o usuário dar o input de outro arquivo pdf para ser analisado.

Explicação do código: No arquivo projeto_alura está um exemplo de código em Python para realizar a tarefa descrita. O código utilizará a biblioteca `PyMuPDF` para ler o arquivo PDF e extrair o texto. Em seguida, ele procura por palavras-chave e frases que indicam a presença de informações sobre concurso público e tenta encontrar os detalhes solicitados.
Deve ser ressaltado que a eficácia do código em extrair informações corretas depende da consistência do formato das informações nos arquivos PDF e pode ser necessário ajustar os padrões de pesquisa e a lógica de extração para funcionar com diferentes layouts.

------------

Análise Detalhada do Código Python

#1. Bibliotecas Importadas:

import fitz  # PyMuPDF

#fitz: Esta biblioteca, baseada no PyMuPDF, é utilizada para interagir com arquivos PDF. Ela fornece ferramentas para abrir, ler, modificar e salvar documentos PDF.

#2. Função extrair_texto_pdf:
def extrair_texto_pdf(caminho_arquivo):
    texto = ''
    with fitz.open(caminho_arquivo) as pdf:
        for pagina in pdf:
            texto += pagina.get_text()
    return texto

# Funcionalidade: Extrai o texto de um arquivo PDF especificado.
# Argumentos:
# caminho_arquivo: A string que representa o caminho do arquivo PDF a ser processado.
# Retorno:
# Uma string contendo todo o texto extraído do PDF, concatenado página por página.
# Explicação:
# A função utiliza o gerenciador de contexto with para abrir o arquivo PDF no modo de leitura.
# O objeto pdf representa o documento PDF aberto.
# Um loop for percorre cada página do PDF armazenada em pagina.
# O método get_text() de cada página é chamado para extrair seu conteúdo textual.
# O texto extraído de cada página é concatenado à variável texto.
# A função retorna a string texto contendo todo o texto extraído do PDF.

# 3. Função encontrar_informacoes_concurso:

def encontrar_informacoes_concurso(texto):
    frases_de_busca = [
        "inscrição para concurso público",
        "vagas para concurso público"
    ]
    if any(frase in texto for frase in frases_de_busca):
        vagas = re.findall("vagas disponíveis: (\d+)", texto, re.IGNORECASE)
        escolaridade = re.findall("grau de escolaridade: (.+?)\n", texto, re.IGNORECASE)
        datas_inscricao = re.findall("inscrições: (\d{2}/\d{2}/\d{4}) a (\d{2}/\d{2}/\d{4})", texto, re.IGNORECASE)
        valor_inscricao = re.findall("valor da inscrição: (R\$[\d\.,]+)", texto, re.IGNORECASE)
        local_inscricao = re.findall("inscreva-se em: (.+?)\n", texto, re.IGNORECASE)
        return {
            "vagas": vagas,
            "escolaridade": escolaridade,
            "datas_inscricao": datas_inscricao,
            "valor_inscricao": valor_inscricao,
            "local_inscricao": local_inscricao
        }
    else:
        return None

# Funcionalidade: Busca e extrai informações relevantes sobre concursos públicos a partir de um texto.
# Argumentos:
# texto: A string contendo o texto extraído do PDF.
# Retorno:
# Um dicionário contendo as informações encontradas sobre o concurso, ou None se nenhuma informação for encontrada.
# Explicação:
# A função define uma lista frases_de_busca contendo frases que indicam a presença de informações sobre concursos.
# Verifica se qualquer frase da lista frases_de_busca está presente no texto usando any().
# Se uma frase de busca for encontrada:
# Utiliza expressões regulares (re.findall) para extrair as informações de vagas, escolaridade, datas de inscrição, valor da inscrição e local de inscrição do texto.
# Armazena as informações extraídas em um dicionário com chaves descritivas.
# Retorna o dicionário contendo as informações do concurso.
# Se nenhuma frase de busca for encontrada:
# Retorna None, indicando que não há informações sobre concursos no texto.

# 4. Função exibir_e_processar_informacoes:

def exibir_e_processar_informacoes(informacoes):
    if informacoes:
        print("Informações encontradas:")
        for chave, valor in informacoes.items():
            print(f"{chave.capitalize()}: {valor}")
    else:
