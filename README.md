# Projeto-1-openLog-Registro-de-Acesso-a-Arquivo-

Objetivo: Criar uma função personalizada em Python que registra acessos a arquivos O que fazer no Google Colab:

Crie um arquivo teste.txt no Google Drive.

Crie um notebook novo no Colab.

Implemente a função openLog(nomearq, modo):

Use open() para abrir o arquivo.

Registre a data e hora de cada acesso no log.txt.

Use o módulo time para isso.

Teste a função acessando o arquivo teste.txt.

No GitHub:

Crie um repositório chamado Acessando_Registro_arquivo.

Salve o notebook do Colab nesse repositório (Arquivo > Salvar uma cópia no GitHub).

Copie o link do repositório.

Célula 1 – Função openLog básica + registro em log.txt
python
Copiar
Editar
import time

def openLog(nomearq, modo):
    # Abre o arquivo solicitado
    arqEntrada = open(nomearq, modo)
    
    # Formata data e hora do acesso
    data_hora = time.strftime("%A, %d %b %Y - %H:%M:%S", time.localtime())
    
    # Cria a linha de log
    linha_log = f"Acesso ao arquivo: {nomearq} | Data e Hora: {data_hora}\n"
    
    # Abre o log e escreve a linha
    with open("log.txt", "a") as log:
        log.write(linha_log)
    
    # Retorna o arquivo aberto
    return arqEntrada
🟢 Célula 2 – Teste da função com um arquivo real
python
Copiar
Editar
# Substitua o caminho pelo caminho real do seu arquivo no Drive
nome_arquivo = "/content/teste.txt"  

# Escrevendo no arquivo com a função openLog
arquivo = openLog(nome_arquivo, "w")
arquivo.write("Teste de acesso ao arquivo com registro em log.")
arquivo.close()

# Agora acessando o mesmo arquivo novamente, modo leitura
arquivo = openLog(nome_arquivo, "r")
print(arquivo.read())
arquivo.close()
🟢 Célula 3 – Verificando o conteúdo do log
python
Copiar
Editar
# Visualiza os registros de acesso
with open("log.txt", "r") as log:
    print("Conteúdo do log de acessos:")
    print(log.read())
