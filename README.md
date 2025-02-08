Sistema Bancário Simples em Python 🏦
Este projeto é um sistema bancário simples desenvolvido em Python, utilizando conceitos fundamentais como estruturas condicionais, loops, interpolação de strings e manipulação de listas.

📌 Funcionalidades
📥 Depósito: Permite adicionar saldo à conta.
💸 Saque: Possui limite de saque diário e verifica saldo antes da operação.
📜 Extrato: Exibe os últimos 5 depósitos e saques realizados.
❌ Encerramento: Opção para sair do sistema.
🛠 Tecnologias utilizadas
Python 3.x
Estruturas de repetição e condicionais
Manipulação de strings e listas



# Menu principal com opções para o usuário escolher! Agora inclui interpolação para exibir o saldo atual sempre que o menu for exibido

menu = """

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

Saldo atual: R$ {saldo:.2f}

=> """


saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opçao = input(menu.format(saldo=saldo))

    if opçao == "d":
        valor = float(input("Informe o valor do depósito:   "))

        if valor > 0:
            saldo += valor

        else:
            print("Operação falhou! O valor é inválido")

    elif opçao == "s":
        valor = float(input("Informe valor de saque:    "))

        excedeu_saldo = valor > saldo
        excedeu_limite = valor > limite
        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou você não tem saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1 

        else:
            print("Operação falhou! O valor informado é inválido")

    elif opçao == "e":
        print("\n================ EXTRATO ================")
        linhas_extrato = extrato.strip().split("\n")[-5:] #Exibição de apenas os últimos 5 registros no extrato
        print("\n".join(linhas_extrato) if extrato else "Não foram realizadas movimentações.")
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")
    
    elif opçao == "q":
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")
