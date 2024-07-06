import pandas as pd
import numpy as np 
import matplotlib.pyplot as plt
import tkinter as tk
from tkinter import Tk
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg
from tkinter.filedialog import askopenfilename

def selecionar():
    root = Tk()
    root.withdraw()
    caminho = askopenfilename(
        filetypes=(('Arquivos CSV', '*.csv'),),
        title='Selecione o arquivo csv '
    )
    

    return caminho

def data_plot():
    caminho = selecionar()

    if caminho:
        dados = pd.read_csv(caminho)
        vendas = dados['vendas'].to_list()
        vendedor = dados['vendedor'].to_list()
        
        fig, grafico = plt.subplots()
        grafico.plot(vendedor, vendas)
        
        janela = tk.Tk()
        janela.title('Gráfico')
        
        
        canvas = FigureCanvasTkAgg(fig, master=janela)
        canvas.draw()
        canvas.get_tk_widget().pack(side=tk.RIGHT, fill=tk.BOTH, expand=True)
        
        janela.mainloop()
    else:
        print('Erro 4004')

def data_bar():
    caminho = selecionar()

    if caminho:
        dados = pd.read_csv(caminho)
        vendas = dados['vendas'].to_list()
        vendedor = dados['vendedor'].to_list()
        
        fig, grafico = plt.subplots()
        grafico.bar(vendedor,vendas, edgecolor='white', linewidth=0.7)
        
        janela = tk.Tk()
        janela.title('Gráfico')
        
        canvas = FigureCanvasTkAgg(fig, master=janela)
        canvas.draw()
        canvas.get_tk_widget().pack(side=tk.RIGHT, fill=tk.BOTH, expand=True)
        
        janela.mainloop()
    else:
        print('Erro 4004')

def data_scatter():
    caminho = selecionar()

    if caminho:
        dados = pd.read_csv(caminho)
        vendas = dados['vendas'].to_list()
        vendedor = dados['vendedor'].to_list()
        
        fig, grafico = plt.subplots()
        grafico.scatter(vendedor,vendas, edgecolor='white', vmin=2, vmax=100)
        
        janela = tk.Tk()
        janela.title('Gráfico')
        
        canvas = FigureCanvasTkAgg(fig, master=janela)
        canvas.draw()
        canvas.get_tk_widget().pack(side=tk.RIGHT, fill=tk.BOTH, expand=True)
        
        janela.mainloop()
    else:
        print('Erro 4004')


def data_stackplot():
    caminho = selecionar()

    if caminho:
        dados = pd.read_csv(caminho)
        vendas = dados['vendas'].to_list()
        vendedor = dados['vendedor'].to_list()
        
        fig, grafico = plt.subplots()
        grafico.stackplot(vendedor,vendas )
        
        janela = tk.Tk()
        janela.title('Gráfico')
        
        
        canvas = FigureCanvasTkAgg(fig, master=janela)
        canvas.draw()
        canvas.get_tk_widget().pack(side=tk.RIGHT, fill=tk.BOTH, expand=True)
        
        janela.mainloop()
    else:
        print('Erro 4004')


def data_stem():
    caminho = selecionar()

    if caminho:
        dados = pd.read_csv(caminho)
        vendas = dados['vendas'].to_list()
        vendedor = dados['vendedor'].to_list()
        
        fig, grafico = plt.subplots()
        grafico.stem(vendedor,vendas )
        
        janela = tk.Tk()
        janela.title('Gráfico')
        
        
        canvas = FigureCanvasTkAgg(fig, master=janela)
        canvas.draw()
        canvas.get_tk_widget().pack(side=tk.RIGHT, fill=tk.BOTH, expand=True)
        
        janela.mainloop()
    else:
        print('Erro 4004')

janela = tk.Tk()
janela.title('Selecionar Arquivo CSV')

bnt1 = tk.Button(janela, text='Carregar Grafico de linhas', command=data_plot)
bnt1.pack(pady=20)

bnt2 = tk.Button(janela, text='Carregar Grafico de barras', command=data_bar)
bnt2.pack(pady=20)

bnt3 = tk.Button(janela, text='Carregar Grafico de bolinha', command=data_scatter)
bnt3.pack(pady=20)

bnt4 = tk.Button(janela, text='Carregar Grafico de ondas', command=data_stackplot)
bnt4.pack(pady=20)

bnt5 = tk.Button(janela, text='Carregar Grafico de linhas com bolinha', command=data_stem)
bnt5.pack(pady=20)

janela.mainloop()
