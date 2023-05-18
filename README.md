# Projeto-python
from tkinter import *
from playsound import playsound #fala da mulher 
from gtts import *
import os #sistema operacional


root = Tk()
root.title('Conversor de Texto para fala')
root.geometry('500x420')
root.maxsize(500, 420)
root.minsize(500, 420)
root.configure(bg='#1d1d1d')

def margem(altura): #aqui estou criando uma função marem, pois preciso dar varias margens ao longo do desenvolvimento do projeto, então quando se cria uma função, tudo fica mias facil (pois asism, é só executar a função)
    tela = Canvas(root, 
                  width=500, 
                  height=altura, 
                  bg= '#1d1d1d', 
                  bd=0, 
                  highlightthickness=0, 
                  relief='ridge')
    tela.pack()
def botao(texto, comando, padx): #aquii estao dando a formatação do botão
    botao= Button(root,
                  text= texto,
                  padx=padx,
                  pady= 20,
                  command=comando,
                  fg= '#FFFFFF',
                  activebackground='#FFFFFF',
                  bg='#C69749',
                  relief=FLAT,
                  font=('Montserrat', 12, 'bold'))
    botao.pack() #uso essa função de execução, para aparecer a minha variavel no front
def inicia ():
    texto_inserido = e_txt.get()
    fala = gTTS(text=texto_inserido, lang='pt', tld='com.br') #configurando a fala da mulher e dando uma função ao botao
    arquivo_fala = 'arquivo_fala.mp3' #criação de um novo arquivo dentro da pasta, arquivo do tipo mp3
    fala.save(arquivo_fala) #aqui vai salvar o arquivo
    playsound(arquivo_fala) #esse playsound serve para quando eu apertar o botão, a mulher do google falar a escrita
def resetar():
    e_txt.delete(0, END) #aqui estou falando para ele deletar do inicio ao fim
    os.remove('arquivo_fala.mp3')#aqui estu falando para ele entrar no sistema operacional e remover o arquivo mp3
margem(20)
titulo = Label (root, #aqui estou dando as especificações do texto que aparecerá no front
                bg='#1d1d1d', 
                fg='#FFFFFF', 
                font=('Montserrat',18,'bold'),
                text='Conversor de texto para fala')
titulo.pack()  #uso essa função de execução, para aparecer a minha variavel no front
margem(30)
insere_texto = Label (root, #aqui estou dando as especificações do texto que aparecerá no front
                bg='#1d1d1d', 
                fg='#FFFFFF', 
                font=('Montserrat',18),
                text='Insira o texto:')
insere_texto.pack()  #uso essa função de execução, para aparecer a minha variavel no front
margem(30)
e_txt = Entry(root,  #aquie estou dando as especificações da minha entrada de texto, ou seja, do meu input (onde o usuário vai digitar o texto que ele desejar)
              width=25, 
              borderwidth=4, 
              relief=FLAT, 
              foreground='#FFFFFF', 
              bg='#000000', 
              font=('Montserrat', 21, 'bold'),
              justify=CENTER)
e_txt.pack()  #uso essa função de execução, para aparecer a minha variavel no front
margem(20)
botao_iniciar = botao('INICIAR', inicia, 37) #aqui estou criando a variavel do botao, e aqui já coloco as suas especificações
margem(10)
botao_reset = botao('RESETAR', resetar, 30)#aqui estou criando a variavel do botao, e aqui já coloco as suas especificações
margem(10)
root.mainloop()

