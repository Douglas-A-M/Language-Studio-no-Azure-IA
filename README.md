# Language-Studio-no-Azure-IA
Com base na quantidade de palavras positivas, negativas ou neutras descritas, irá ser obtido um sentimento sobre o mesmo descrito.

import re

def analise_sentimento(comentario):
    palavras = re.findall(r'\b\w+\b', comentario.lower())
    
    positivas = ["bom", "belo","boa", "ótimo", "excelente", "maravilhoso", "gostei", "incrível", "amei", "amo", "incrivel", "fantástico", "feliz","alegre"]
    negativas = ["ruim", "péssimo", "horrível", "terrível", "odeio", "triste", "chateado", "lamentável", "decepcionado"]
    neutras = ["mas", "deixou", "apesar", "embora", "mediano", "apenas", "contudo", "todavia"]

    count_positivo = sum(palavra in positivas for palavra in palavras)
    count_negativo = sum(palavra in negativas for palavra in palavras)
    count_neutro = sum(palavra in neutras for palavra in palavras)

    if count_positivo > count_negativo and count_neutro == 0:
        return "Positivo, ja disse tudo, vamos manter o ritmo e fazer desse um ótimo dia ou semana."
    elif count_negativo > count_positivo and count_neutro == 0:
        return "Negativo, Vamos melhorar esse astral e ir em busca de melhorias e coisas boas."
    else:
        return "Neutro, Vamos elevar nosso humor e fazer desse um ótimo dia."

if __name__ == "__main__":
    comentario = input("Digite uma frase")
    sentimento = analise_sentimento(comentario)
    print("Com base na sua frase, hoje você está:", sentimento)
