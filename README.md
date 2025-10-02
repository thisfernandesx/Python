pacientes = []


def cadastrar_paciente():
    nome = input("Nome do paciente: ")
    idade = int(input("Idade: "))
    telefone = input("Telefone: ")
    pacientes.append({"nome": nome, "idade": idade, "telefone": telefone})
    print("Paciente cadastrado com sucesso!")


def ver_estatisticas():
    if not pacientes:
        print("Nenhum paciente cadastrado.")
        return
    total = len(pacientes)
    media = sum(p["idade"] for p in pacientes) / total
    mais_novo = min(pacientes, key=lambda x: x["idade"])
    mais_velho = max(pacientes, key=lambda x: x["idade"])
    print(f"Total de pacientes: {total}")
    print(f"Idade média: {media:.1f}")
    print(f"Paciente mais novo: {mais_novo['nome']} ({mais_novo['idade']} anos)")
    print(f"Paciente mais velho: {mais_velho['nome']} ({mais_velho['idade']} anos)")


def buscar_paciente():
    nome = input("Digite o nome do paciente: ")
    encontrado = [p for p in pacientes if p["nome"].lower() == nome.lower()]
    if encontrado:
        for p in encontrado:
            print(f"Nome: {p['nome']} | Idade: {p['idade']} | Telefone: {p['telefone']}")
    else:
        print("Paciente não encontrado.")


def listar_pacientes():
    if not pacientes:
        print("Nenhum paciente cadastrado.")
    for p in pacientes:
        print(f"Nome: {p['nome']} | Idade: {p['idade']} | Telefone: {p['telefone']}")


while True:
    print("\n=== SISTEMA CLÍNICA VIDA+ ===")
    print("1. Cadastrar paciente")
    print("2. Ver estatísticas")
    print("3. Buscar paciente")
    print("4. Listar todos os pacientes")
    print("5. Sair")
    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        cadastrar_paciente()
    elif opcao == "2":
        ver_estatisticas()
    elif opcao == "3":
        buscar_paciente()
    elif opcao == "4":
        listar_pacientes()
    elif opcao == "5":
        print("Encerrando o sistema.")
        break
    else:
        print("Opção inválida. Tente novamente.")
