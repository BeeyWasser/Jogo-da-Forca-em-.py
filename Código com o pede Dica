# Importando a biblioteca para gerar números aleatórios
import random

# Constante que define o número máximo de tentativas
MAX_TENTATIVAS = 7

# Imprimindo a mensagem de abertura do jogo
def imprime_mensagem_abertura():
    print("Bem vindo ao jogo da Forca!")

# Função que cria uma lista com underlines para representar letras não descobertas
def inicializa_letras_acertadas(palavra):
    return ["_" for letra in palavra]

# Função que pede uma letra ao jogador
def pede_chute(palavra_secreta, letras_acertadas):
    chute = input("Qual letra? Se desejar digite DICA. ")  # Pede a letra
    chute = chute.strip().upper()  # Remove espaços e coloca em maiúsculo
    return chute

# Função que marca a letra correta se ela estiver na palavra
# Percorre a palavra e substitui o underline pela letra chutada

def marca_chute_correto(chute, letras_acertadas, palavra):
    for i in range(len(palavra)):
        if chute == palavra[i]:
            letras_acertadas[i] = chute

# Função que imprime mensagem de vitória
def imprime_mensagem_vencedor():
    print("Parabéns, você ganhou!")

# Função que imprime mensagem de derrota e mostra a forca
def imprime_mensagem_perdedor(palavra):
    print("Puxa, você foi enforcado!")
    print(f"A palavra era {palavra}")
    print("""
        _______________        
       /               \\
      /                 \\
    //                   \\/\\  
    \\|  XXXX     XXXX   | /   
     |   XXXX     XXXX   |/    
     |   XXX       XXX   |     
     |                   |     
     \\__     XXX      __/     
       |\\    XXX     /|       
       | |           | |       
       | I I I I I I |        
       |  I I I I I  |        
       \\_           _/        
         \\_______/           
    """)

# Função que desenha a forca com base no número de erros
def desenha_forca(erros):
    print("  _______     ")
    print(" |/      |    ")

    if erros >= 1:
        print(" |      (_)   ")  # Cabeça
    else:
        print(" |            ")

    if erros == 2:
        print(" |       |    ")  # Tronco
    elif erros == 3:
        print(" |      \\|    ")  # Um braço
    elif erros >= 4:
        print(" |      \\|/   ")  # Dois braços
    else:
        print(" |            ")

    if erros >= 5:
        print(" |       |    ")  # Corpo
    else:
        print(" |            ")

    if erros == 6:
        print(" |      /     ")  # Uma perna
    elif erros == 7:
        print(" |      / \\   ")  # Duas pernas
    else:
        print(" |            ")

    print(" |            ")
    print("_|___         ")
    print()

# Função principal do jogo
def jogar():
    imprime_mensagem_abertura()

    # Lista de palavras lidas de um arquivo
    palavras = []
    with open("palavras.txt", "r") as arquivo:
        for linha in arquivo:
            palavras.append(linha.strip())  # Remove quebra de linha e adiciona à lista

    # Escolhe uma palavra secreta aleatória
    palavra_secreta = random.choice(palavras).upper()

    # Inicializa com underlines
    letras_acertadas = inicializa_letras_acertadas(palavra_secreta)

    erros = 0
    enforcou = False
    acertou = False

    # Enquanto o jogador não perder nem ganhar
    while not enforcou and not acertou:
        print("\nPalavra: ", " ".join(letras_acertadas))  # Mostrando a palavra atual
        
        # Validar a entrada
        while True:
            chute = pede_chute(palavra_secreta, letras_acertadas)  # Pedindo uma letra 

            if (len(chute) == 1 and chute.isalpha()) or (chute == "DICA"):
                break
        
        if chute == "DICA":
            # Dica: revela uma letra da palavra no início do jogo
            letra_dica = random.choice(palavra_secreta)
            print(f"\nDica: A palavra contém a letra '{letra_dica}'")
            marca_chute_correto(letra_dica, letras_acertadas, palavra_secreta)

        else:
            if chute in palavra_secreta:
                marca_chute_correto(chute, letras_acertadas, palavra_secreta)  # Marca se acertar
            else:
                erros += 1
                desenha_forca(erros)  # Desenha a forca se o usuário errar kk
                print(f"Você ainda tem {MAX_TENTATIVAS - erros} tentativa(s)") # imprime a quant. de tentativas disp.

        enforcou = erros == MAX_TENTATIVAS
        acertou = "_" not in letras_acertadas

    # Resultado final
    if acertou:
        imprime_mensagem_vencedor()
        print(f"A palavra era {palavra_secreta}")
    else:
        imprime_mensagem_perdedor(palavra_secreta)

    print("\nFim do jogo.")

# Linha que executa o jogo quando o arquivo é rodado diretamente
if __name__ == "__main__":
    jogar()
