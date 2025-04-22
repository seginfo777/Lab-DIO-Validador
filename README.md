# Lab-DIO-Validador
Projeto do validador de bandeira de cartão de crédito

Código finalizado e funcional:

import re

def identificar_bandeira(numero):
    numero = re.sub(r'\D', '', numero)

    bandeiras = [
        ("Visa", re.compile(r"^4\d{12}(\d{3})?$")),
        ("MasterCard", re.compile(r"^5[1-5]\d{14}$")),
        ("American Express", re.compile(r"^3[47]\d{13}$")),
        ("Elo", re.compile(r"^(4011(78|79)|4312(74|75)|4389(35|36)|4514(16|17)|4576(31|32)|5041(75|76)|5067(99|98)|5090(41|42)|6277(80|81)|6362(97|98)|6363(68|69)|650\d{2}|6516[5-9]|6550[0-9])\d{10}$")),
        ("Hipercard", re.compile(r"^(606282\d{10}(\d{3})?)|(3841\d{15})$")),
        ("Diners Club", re.compile(r"^3(?:0[0-5]|[68]\d)\d{11}$")),
        ("Discover", re.compile(r"^6(?:011|5\d{2})\d{12}$")),
        ("JCB", re.compile(r"^(?:2131|1800|35\d{3})\d{11}$")),
        ("Aura", re.compile(r"^50[0-9]{14,17}$")),
        ("Banescard", re.compile(r"^6034(94|95)\d{10}$"))
    ]

    for nome, padrao in bandeiras:
        if padrao.match(numero):
            return nome

    return "Bandeira desconhecida"


# Exemplo de uso
if __name__ == "__main__":
    numero = input("Digite o número do cartão de crédito: ")
    resultado = identificar_bandeira(numero)
    print(f"Bandeira identificada: {resultado}")
