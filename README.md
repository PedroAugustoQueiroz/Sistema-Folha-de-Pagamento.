# Sistema-Folha-de-Pagamento.
Um sistema montado para gerar uma folha de pagamento.

#(PYTHON)

ganho_Hora = float (input(f"Quanto é pago por hora? "))
horas_Trab_Dia = int (input(f"Quantas horas são trabalhadas no mês? "))
salario_Bruto = (ganho_Hora*horas_Trab_Dia)

#DESCONTO POR FALTAS NÃO JUSTIFICADAS
faltas_NaoJustifi = int (input(f"Digite a quantidade de faltas não justificadas: "))
desconto_Faltas = (salario_Bruto/30)*faltas_NaoJustifi

#SALÁRIO FAMÍLIA
filhos = int (input(f"Quantos filhos menores de 14 anos o funcionário tem? "))
if (salario_Bruto<=1754.18 and filhos >= 1):
    salario_Familia = (59.82*filhos)
elif (salario_Bruto<=1754.18 and filhos==0):
    print (f"Não há aumento de Salário Família para este funcionário! ")
else:
    print (f"Não há aumento de Salário Família para este funcionário! ")
    salario_Familia = 0

#FGTS
fgts = (salario_Bruto/100)*8

#IMPOSTO DE RENDA (IR)
if (salario_Bruto>=1903.99 and salario_Bruto<=2826.65):
    percentual_ir=7.50
    ir=(salario_Bruto*7.50)/100
elif (salario_Bruto>=2826.66 and salario_Bruto<=3751.05):
    percentual_ir=15
    ir=(salario_Bruto*15)/100
elif (salario_Bruto>=3751.06 and salario_Bruto<=4664.68):
    percentual_ir=22.50
    ir=(salario_Bruto*22.50)/100
elif (salario_Bruto>=4664.68):
    percentual_ir=27.50
    ir=(salario_Bruto*27.50)/100
else:
    print(f"Não há descontos de IR para este salário.")
    ir=0

#CONTRIBUIÇÃO INSS
if (salario_Bruto>=1320.00):
    percentual_inss=7.50
    inss=(salario_Bruto*7.50)/100
elif (salario_Bruto>=1320.99 and salario_Bruto<=2571.28):
    percentual_inss=9
    inss=(salario_Bruto*9)/100
elif (salario_Bruto>=2571.29 and salario_Bruto<=3856.93):
    percentual_inss=12
    inss=(salario_Bruto*12)/100
elif (salario_Bruto>=3856.94 and salario_Bruto>=7507.49):
    percentual_inss=14
    inss=(salario_Bruto*14)/100
else:
    print(f"Não há descontos de INSS para este salário.")
    inss=0
    
sindicato = (5*salario_Bruto)/100

descontos_Totais = (ir+inss+sindicato)
salario_liquido = (salario_Bruto-descontos_Totais)


#AUMENTOS
if (salario_liquido<=280):
    percentual=20
    aumento=(salario_liquido/100)*20
    novo_salario=salario_liquido+aumento
elif (salario_liquido>280 and salario_liquido<=700):
    percentual=15
    aumento=(salario_liquido/100)*15
    novo_salario=salario_liquido+aumento
elif (salario_liquido>700 and salario_liquido<=1500):
    percentual=10
    aumento=(salario_liquido/100)*10
    novo_salario=salario_liquido+aumento
elif (salario_liquido>1500):
    percentual=5
    aumento=(salario_liquido/100)*5
    novo_salario=salario_liquido+aumento
else:
    print(f"Não há ajustes para este salário.")
    novo_salario=0
    
print(f"* salário bruto: R${salario_Bruto:.2f}\n * imposto de renda: - R${ir:.2f}\n * INSS: - R${inss:.2f}\n * imposto sindical:  - R${sindicato:.2f}\n * FGTS: - R${fgts:.2f}\n * quantidade de faltas não justificadas: {faltas_NaoJustifi}\n * valor descontado pelas faltas: - R${desconto_Faltas:.2f}\n * salário liquido anterior: R${salario_liquido:.2f}\n * percentual de aumento: + {percentual}%\n * valor do aumento em reais: + R${aumento:.2f}\n * Salário Família: + R${salario_Familia:.2f}\n * novo salário líquido: R${(novo_salario + salario_Familia):.2f}\n * novo salário bruto: {(salario_Bruto + aumento+ salario_Familia):.2f}.")
