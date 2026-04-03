# CALCULADORA_CIENT-FICA
Esta calculadora científica em Python utiliza o módulo math para realizar operações aritméticas, trigonométricas (convertendo graus em radianos), logarítmicas e fatoriais. Possui interface via terminal com menu interativo, tratamento de exceções para entradas inválidas e proteção contra divisões por zero, garantindo robustez e precisão.

import math

def exibir_menu():
    print("\n" + "="*30)
    print("   CALCULADORA CIENTÍFICA")
    print("="*30)
    print("1. Adição (+)      | 7. Seno (sin)")
    print("2. Subtração (-)   | 8. Cosseno (cos)")
    print("3. Multiplicação(*)| 9. Tangente (tan)")
    print("4. Divisão (/)     | 10. Logaritmo (log)")
    print("5. Potência (x^y)  | 11. Raiz Quadrada (sqrt)")
    print("6. Fatorial (n!)   | 0. Sair")
    print("="*30)

def calculadora():
    while True:
        exibir_menu()
        opcao = input("Escolha uma operação: ")

        if opcao == '0':
            print("Encerrando... Até logo!")
            break

        try:
            if opcao in ['1', '2', '3', '4', '5']:
                num1 = float(input("Primeiro número: "))
                num2 = float(input("Segundo número: "))

                if opcao == '1': print(f"Resultado: {num1 + num2}")
                elif opcao == '2': print(f"Resultado: {num1 - num2}")
                elif opcao == '3': print(f"Resultado: {num1 * num2}")
                elif opcao == '4': 
                    if num2 == 0: print("Erro: Divisão por zero!")
                    else: print(f"Resultado: {num1 / num2}")
                elif opcao == '5': print(f"Resultado: {math.pow(num1, num2)}")

            elif opcao in ['6', '7', '8', '9', '11']:
                val = float(input("Digite o valor: "))

                if opcao == '6': print(f"Resultado: {math.factorial(int(val))}")
                elif opcao == '7': print(f"Resultado: {math.sin(math.radians(val))}")
                elif opcao == '8': print(f"Resultado: {math.cos(math.radians(val))}")
                elif opcao == '9': print(f"Resultado: {math.tan(math.radians(val))}")
                elif opcao == '11': print(f"Resultado: {math.sqrt(val)}")

            elif opcao == '10':
                val = float(input("Valor do logaritmando: "))
                base = input("Base (padrão é 'e', digite um número para outra base): ")
                if base == '' or base.lower() == 'e':
                    print(f"Resultado: {math.log(val)}")
                else:
                    print(f"Resultado: {math.log(val, float(base))}")
            else:
                print("Opção inválida!")

        except ValueError:
            print("Erro: Por favor, insira apenas números válidos.")
        except Exception as e:
            print(f"Ocorreu um erro: {e}")

if __name__ == "__main__":
    calculadora()
