# 📌 Legenda de Siglas + Métricas de Classificação (guia rápido)

Este material serve como “cola oficial” para ler **matriz de confusão**, `classification_report` e discutir erros do modelo em linguagem humana.

---

## 1) 🧩 Siglas básicas (matriz de confusão)

Considere um problema de **classificação binária**:

- **Classe Positiva (1)**: o evento que estamos “procurando”  
  Ex.: *“sobreviveu”*, *“é spam”*, *“tem doença”*, *“é fumante”*
- **Classe Negativa (0)**: o contrário  
  Ex.: *“não sobreviveu”*, *“não é spam”*, *“não tem doença”*, *“não é fumante”*

### ✅ TP, TN, FP, FN (o coração do assunto)

| Sigla | Nome (PT) | O que significa (frase curta) | Interpretação humana |
|------:|-----------|--------------------------------|----------------------|
| **TP** | True Positive (*Verdadeiro Positivo*) | Era **positivo** e o modelo previu **positivo** | “Acertou um caso positivo” |
| **TN** | True Negative (*Verdadeiro Negativo*) | Era **negativo** e o modelo previu **negativo** | “Acertou um caso negativo” |
| **FP** | False Positive (*Falso Positivo*) | Era **negativo**, mas o modelo previu **positivo** | “Alarme falso” |
| **FN** | False Negative (*Falso Negativo*) | Era **positivo**, mas o modelo previu **negativo** | “Perdeu um positivo” |

> **Tradução rápida:**  
> - **FP** = o modelo “acusou” algo que não era  
> - **FN** = o modelo “deixou passar” algo que era

---

## 2) 📦 Matriz de confusão (formato padrão)

Quando as classes são `{0, 1}`, muitas bibliotecas usam:


[[TN, FP], [FN, TP]]
Ou seja:
- Linha 0 = casos reais **negativos**
- Linha 1 = casos reais **positivos**
- Coluna 0 = predição **negativa**
- Coluna 1 = predição **positiva**

---

## 3) 📏 Métricas principais (com fórmula e significado)

> Todas usam TP/TN/FP/FN como “ingredientes”.

### 🎯 Acurácia (Accuracy)
- **Fórmula:** (TP + TN) / (TP + TN + FP + FN)  
- **O que mede:** proporção total de acertos.  
- **Cuidado:** pode enganar em dados desbalanceados (ex.: “sempre prever 0”).

---

### ✅ Precisão (Precision)
- **Fórmula:** TP / (TP + FP)  
- **O que mede:** quando o modelo diz **“positivo”**, com que frequência ele está certo?  
- **Quando é crucial:** quando **FP é caro** (ex.: acusar inocentes, alarme falso caro, reprovar quem deveria passar).

---

### 🔎 Recall (Sensibilidade / TPR)
- **Siglas:**  
  - **TPR** = *True Positive Rate*  
  - **Recall** = Sensibilidade  
- **Fórmula:** TP / (TP + FN)  
- **O que mede:** de todos os positivos reais, quantos o modelo conseguiu capturar?  
- **Quando é crucial:** quando **FN é caro** (ex.: deixar passar doença, não detectar fraude, “perder sobreviventes”).

---

### 🧊 Especificidade (Specificity / TNR)
- **Siglas:**  
  - **TNR** = *True Negative Rate*  
  - **Specificity** = Especificidade  
- **Fórmula:** TN / (TN + FP)  
- **O que mede:** de todos os negativos reais, quantos o modelo reconhece corretamente?  
- **Quando é crucial:** quando você quer **minimizar FP**.

---

### ⚖️ F1-Score
- **Fórmula:** 2 × (Precisão × Recall) / (Precisão + Recall)  
- **O que mede:** equilíbrio entre precisão e recall.  
- **Quando é útil:** principalmente com **classes desbalanceadas**.

---

## 4) 🧾 Siglas comuns no `classification_report` (Scikit-learn)

| Termo | Significado | Em português |
|------|-------------|-------------|
| **precision** | Precisão | “Confiabilidade do positivo” |
| **recall** | Recall / Sensibilidade / TPR | “Capacidade de capturar positivos” |
| **f1-score** | F1 | “Equilíbrio entre precision e recall” |
| **support** | Quantidade de exemplos reais daquela classe | “Tamanho real da classe” |
| **macro avg** | Média simples entre classes (todas pesam igual) | boa quando classes são desbalanceadas |
| **weighted avg** | Média ponderada pelo suporte (classes maiores pesam mais) | reflete a distribuição real |

---

## 5) 🧠 Como interpretar erros (modelo mental em 2 linhas)

- Se você quer **“não deixar passar positivos”** → foque em **reduzir FN** (aumentar recall).  
- Se você quer **“evitar alarmes falsos”** → foque em **reduzir FP** (aumentar precisão/especificidade).

---

## 6) Exemplo de interpretação humana (genérico)
Suponha que a classe 1 significa “evento importante”:

- **FN alto**: “o modelo está deixando passar casos importantes”  
- **FP alto**: “o modelo está gritando ‘evento!’ quando não é”

---

## 7) Mini-glossário (toda sigla que costuma aparecer)

- **TP**: True Positive (Verdadeiro Positivo)  
- **TN**: True Negative (Verdadeiro Negativo)  
- **FP**: False Positive (Falso Positivo)  
- **FN**: False Negative (Falso Negativo)  
- **TPR**: True Positive Rate (= Recall/Sensibilidade)  
- **TNR**: True Negative Rate (= Specificity/Especificidade)  
- **FPR**: False Positive Rate = FP / (FP + TN)  
- **FNR**: False Negative Rate = FN / (FN + TP)  
- **ACC**: Accuracy (Acurácia)  
- **P**: Precision (Precisão)  
- **R**: Recall (Recall/Sensibilidade)  

---

