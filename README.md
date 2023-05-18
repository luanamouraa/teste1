# teste1
Primeiro uso do GitHub. 
streamlit teste luana
import matplotlib.pyplot as plt
from PIL import Image
import numpy as np
from wordcloud import WordCloud, ImageColorGenerator

stopwords = []

arqstop = open('stopwords.txt', encoding='utf-8')

for linha in arqstop:
    stopwords.append(linha.replace('\n', '').replace(' ' , ''))
    stopwords += ['linha', 'in', 'and', 'the', 'n', 'pp', 'of', 'op']

lista = linha.split(' ')
nova_lista = []
for palavra in lista:
     if len(palavra) > 3:        
        nova_lista.append(palavra)
        nova_linha = ' '
        nova_linha += palavra + ' '

mask = np.array(Image.open('livrodesenho.png'))
wordcloud = WordCloud(stopwords=stopwords,
                    background_color="pink", mask=mask, width=1600,
                      height=800, max_words=1000, max_font_size=500,
                      min_font_size=1, contour_width=5, contour_color='black')

image = ImageColorGenerator(mask)
wordcloud.generate_from_text(texto)
plt.figure(figsize = (15, 10)) #tamanho do gráfico
plt.imshow(wordcloud, interpolation = 'bilinear') # plotagem da nuvem de palavras
plt.axis('off') # remove as bordas
plt.show() # mostra a word cloud)
