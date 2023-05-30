# Module3Week2
"""
Para a atividade dessa semana, vamos trabalhar com a seguinte situação:
Uma pessoa do seu time de desenvolvimento está escrevendo várias funções
que calculam diferentes formas de gerar juros. Veja abaixo o exemplo de uma das funções:

def juros_simples (capital, taxa, tempo):
resultado = capital* (taxa/100) * tempo
return resultado

Ela pediu para você escrever um decorator chamado decorator_imprimir,
que será usado para a função chamada imprima os parâmetros: capital, taxa e tempo,
além do resultado da função.
Ao executar a função juros_simples, teríamos o seguinte resultado:

CAPITAL: 1000 TAXA: 5 TEMPO: 6 RESULTADO: 300.0

Com isso, será criada uma função decoradora (decorator) chamada decorator_imprimir que, ao ser usada com qualquer
função parecida com a juros_simples (isto é, uma função que receba 3 parâmetros — capital, taxa, tempo),
seja retornado um valor numérico correspondente ao juros.
"""

def decorador_imprimir(func):
    # Decorador que imprime os resultados de juros de uma função original.

    def calcu_juros(*args, **kwargs):
        # Função interna que recebe e imprime os valores da função original.
        
        # Salvando os valores dos parámetros da função original na variavél args.  
        capital, taxa, tempo = args
    
        """
        É possível também salvar os dados com iteação por lista:
        
        capital = args[0]
        taxa = args [1]
        tempo = args [0]
        """ 
        
        # Levando a variavel para se exceutada pelo decorador na variavél resultado.
        resultado = func(*args, **kwargs)

        # Responsável de imprimir os valores dos parámetros.
        print("CAPITAL: ", capital, "TAXA: ", taxa , "TEMPO: ", tempo, "RESULTADO: ", resultado)
        
        return resultado
    return calcu_juros

@decorador_imprimir:
def juros_simples (capital, taxa, tempo):
    # função que calcula juros simples.
    
    # Instanciamos a operação a realizar:
    resultado = capital* (taxa/100) * tempo
    return resultado

juros_simples (1000,5,6)
