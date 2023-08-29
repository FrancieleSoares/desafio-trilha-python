# desafio-trilha-python
import textwrap

def menu():
    menu = """\n
    *****************MENU*****************

    [d]\tDepositar
    [s]\tSacar
    [e]\tExtrato
    [nc]\tNova conta
    [lc]\tListar contas
    [nu]\tNovo usuário
    [q]\tSair

    => """
return input(textwrap.dedent(menu))

def depositar(saldo, valor, extrato,/):
    if valor > 0:
        saldo += valor 
        extrato += f'Depósito:\tR$ {valor:.2f}\n'
        print('\n===Depósito realizado com sucesso!===')
    else:
        print('\nOperação falhou! O valor informado á inválido.')
        
    return saldo, extrato 
        
def sacar(*, saldo, valor, extrato, limite, numero_saques, limite_saques):
    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

        else:
            print("Operação falhou! O valor informado é inválido.")

        
def exibir_extrato(saldo, /, *, extrato):
    
def criar_usuario(usuarios):
    cpf = input('Informe o CPF (Somente números): ')
    usuario = filtrar_usuario(cpf, usuarios)
    
    if usuario:
        print('\nUsuário já existente com esse CPF!')
        return
    
    nome = input('Informe o nome completo: ')
    data_nascimento = input('Informe sua data de nascimento (dd-mm-aaaa): ')
    endereco = input('Informe o endereço (Logradouro, número - bairro - cidade/sigla estado): ')
    
    usuarios.append({'nome': nome, 'data_nascimento': data_nascimento, 'cpf': cpf, 'endereco': endereco})
    
    print('===Usuário criado com sucesso!===')
    
def filtrar_usuario(cpf, usuarios):
    usuarios_filtrados = [usuario for usuario in usuarios if usuario['cpf'] == cpf]
    return usuarios_filtrados[0] else None

def criar_conta(agencia, numero_conta, usuarios):
    cpf = input('Informe o CPF do usuario: ')
    usuario = filtrar_usuario(cpf, usuarios)
    
    if usuario:
        print('\n===Conta criada com sucesso!===')
        return {'agencia': agencia, 'numero_conta': numero_conta, 'usuario': usuario}
    print('\n Usuário não encontrado, fluxo de criação de conta encerrado!')
    
def listar_contas(contas):
    for conta in contas:
        linha = f'''\
            Agência:\t{conta['agencia']}
            C/C:\t{conta['numero_conta']}
            Titular:\t{conta['usuario']['nome']}
        '''
        print('=' * 100)
        print(textwrap.dedent(linha))


def main():
    LIMITE_SAQUES = 3
    AGENCIA = '0001' 
      
    saldo = 0
    limite = 500
    extrato = ""
    numero_saques = 0
    usuarios = []
    contas =[]


while True:

    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Informe o valor do depósito: "))


        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"
            print('\n====Depósito realizado com sucesso!====')
        else:
            print("Operação falhou! O valor informado é inválido.")
        


    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "e":
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")
    elif opcao == 'nu':
        
    elif opcao == 'nc':
        numero_conta = len(contas) + 1
        conta = criar_conta(AGENCIA, numero_conta, usuarios)
        
        if conta:
            contas.append(conta)
            
        elif opcao == 'lc':
            listar_contas(contas)
    
    elif opcao == "q":
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")

main()
