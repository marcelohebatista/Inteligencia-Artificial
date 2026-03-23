# 🧪 Atividade_001 — Pipeline de Classificação (com dataset do Seaborn)

**Disciplina:** Inteligência Artificial  
**Professor:** Marcelo Batista  

---

## 🎯 Objetivo da atividade

Escolher **um dataset do Seaborn** (exceto *iris* e *titanic*) e construir um experimento de **classificação** seguindo o padrão “mínimo profissional”:

**Dados → Treino → Teste**  
com **pré-processamento correto** (missing values + colunas categóricas)  
e **avaliação interpretável** (métricas + matriz de confusão + interpretação humana dos erros).

---

## ✅ Escolha do dataset (obrigatório)

Escolha **1** dataset do Seaborn que permita **classificação**.

### Sugestões seguras (recomendadas)
- **`penguins`**  
  - *Target sugerido:* `species` (classificação multiclasse)
- **`tips`**  
  - *Target sugerido:* `smoker` (classificação binária)

> **Regra:** não use *iris* e não use *titanic* nesta atividade.

---

## 🧠 Parte 1 — Definição do problema (em Markdown no topo do seu notebook)
Escreva um pequeno “contrato do projeto” respondendo:

1) **Dataset escolhido**  
2) **Qual é o target (y)** que você quer prever  
3) O problema é classificação  
4) Quais colunas serão usadas como **features (X)**  
5) Quais colunas você vai **remover** e por quê (ex.: colunas inúteis, texto livre, identificadores)

---

## 🧹 Parte 2 — Diagnóstico dos dados (obrigatório)
Você deve mostrar evidências de que entendeu o dataset, incluindo:

- Tamanho do dataset (quantas linhas e colunas)
- Tipos das colunas (numéricas vs categóricas vs booleanas)
- Quantidade de **missing values** por coluna
- Distribuição do target (quantos exemplos em cada classe)

**Por que isso importa?**  
Porque um bom pipeline nasce do diagnóstico: se tem missing, precisa imputar; se tem texto/categorias, precisa codificar.

---

## 🧱 Parte 3 — Construção do Pipeline (obrigatório)
Você deve construir um pipeline que trate corretamente:

### 1) Colunas numéricas
- Preencher faltantes (ex.: mediana)
- Normalizar/Padronizar (scaling)

### 2) Colunas categóricas e booleanas
- Preencher faltantes (ex.: valor mais frequente)
- Transformar em números (one-hot)

### 3) Experimento reprodutível
- Separar em **treino** e **teste**
- Garantir que o pré-processamento **aprenda apenas no treino** e **aplique no teste**
- Usar semente fixa (reprodutibilidade)

> **Critério de qualidade:** seu pipeline não pode “olhar” o teste antes da hora.

---

## 🤖 Parte 4 — Modelos (baseline + melhoria) (obrigatório)
Treine e compare **dois modelos**, mudando **somente o classificador** (para a comparação ser justa):

1) **Baseline (obrigatório):** um modelo simples e interpretável  
2) **Melhoria simples (obrigatório):** um modelo mais potente

Explique em 2–3 linhas por que você considerou um “baseline” e o outro “melhoria”.

---

## 📏 Parte 5 — Avaliação (obrigatório)
No conjunto de **teste**, apresente:

- **Accuracy**
- **Classification report** (precision/recall/F1 por classe)
- **Matriz de confusão**
- Para classificação binária: **TN / FP / FN / TP**

> Se for multiclasse, a matriz de confusão continua obrigatória, mas TN/FP/FN/TP não se aplica da mesma forma “direta”.

---

## 🧠 Parte 6 — Interpretação humana dos erros (obrigatório)
Aqui está a parte mais importante da atividade.

Escreva uma interpretação em linguagem humana:

- O que significa um **FP** no seu problema?
- O que significa um **FN** no seu problema?
- Qual erro é mais “grave” no contexto do dataset escolhido?
- O modelo baseline errou mais em qual classe? E o modelo melhorado?

### Exemplos de interpretação (para guiar seu texto)
- Se o target for `smoker` (classe 1 = fumante):  
  - **FN:** fumantes reais que o modelo disse que “não fumam”  
  - **FP:** não fumantes que o modelo acusou como “fumantes”

- Se o target for `species` (pinguins):  
  - O erro significa “o modelo confundiu espécie A com espécie B” (e isso pode ter relação com variáveis parecidas, missing, ou ruído).

---

## ✅ Entrega (o que será avaliado)
Você deve entregar um notebook com:

- Definição do problema (target + justificativa)
- Diagnóstico do dataset (tipos, missing, distribuição do target)
- Pipeline completo (numéricas + categóricas)
- Treino e avaliação de **2 modelos**
- Métricas no teste + matriz de confusão
- Interpretação humana dos erros (FP/FN ou confusões entre classes)

---

## ⭐ Critério de excelência (vale ponto extra)
- Você identifica **uma limitação** do dataset escolhido (ex.: tamanho pequeno, desbalanceamento, missing forte, colunas redundantes)
- Você sugere **uma melhoria simples** (ex.: ajustar hiperparâmetros, testar outro modelo, revisar features)

---

