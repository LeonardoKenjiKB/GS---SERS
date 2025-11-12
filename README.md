import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv("consumo_energia_industrial.csv")
df.head()

# Boxplot
plt.figure(figsize=(12,5))
sns.boxplot(x=df["Tipo_de_uso"], y=df["Consumo_kWh"], data=df[["Tipo_de_uso","Consumo_kWh"]])
plt.title("Distribuição por tipo de uso")
plt.show()

# Correlação
plt.figure(figsize=(4,3))
matriz_corr = df[["Gasto_R$", "Impacto_ambiental_kgCO2", "Desperdicio_kWh"] + ["Consumo_kWh"]].corr()
sns.heatmap(matriz_corr,annot=True,cmap="coolwarm", fmt=".2f")
plt.title("Correlação entre Atributos numéricos e rótulo", fontweight="bold")
plt.show()
