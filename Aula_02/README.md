# Aula 02 — Titanic (Pipeline “mínimo profissional”) — Resumo

**Disciplina:** Inteligência Artificial  
**Professor:** Marcelo Batista  

## 🎯 Objetivos da aula
- Utilizar o **dataset Titanic** para um problema real de classificação
- Manipular dados com **Pandas/Seaborn**
- Treinar um **modelo baseline** (Logistic Regression)
- Consolidar o fluxo: **Dados → Treino → Teste**
- Construir um **pipeline reprodutível** com `Pipeline` + `ColumnTransformer`
- Avaliar o modelo com métricas e **interpretar erros (FP/FN)**

---

## 📦 Dataset
- Fonte: `sns.load_dataset("titanic")`
- Target (**y**): `survived` (0 = não sobreviveu, 1 = sobreviveu)
- Coluna removida: `alive` (redundante com o alvo)
- Características do mundo real:
  - **missing values** (ex.: `age`, `deck`, `embarked`)
  - **colunas categóricas** (ex.: `sex`, `embark_town`, `class`)
  - dados com **viés histórico** (classe social, “mulheres e crianças primeiro”)

---

## 🧱 Por que usar Pipeline + ColumnTransformer?
Em dados reais, cada tipo de coluna precisa de um tratamento diferente:

### Numéricas
- `SimpleImputer(strategy="median")` para faltantes
- `StandardScaler()` para padronização (ajuda especialmente em modelos lineares)

### Categóricas / booleanas
- `SimpleImputer(strategy="most_frequent")`
- `OneHotEncoder(handle_unknown="ignore")` para converter texto em números

**Benefícios:**
- evita “bagunça” no notebook
- reduz risco de **data leakage**
- garante reprodutibilidade e facilita troca de modelos

---

## 🔁 Fluxo sagrado (aplicado no Titanic)
1. Carregar e inspecionar os dados (shape, tipos, faltantes)
2. Separar `X` e `y`
3. Dividir em treino/teste com reprodutibilidade:
   - `test_size=0.2`
   - `random_state=42`
   - `stratify=y`
4. Criar o `preprocess = ColumnTransformer([...])`
5. Montar o `model = Pipeline([("prep", preprocess), ("clf", ...)])`
6. Treinar (`fit`) no treino
7. Prever (`predict`) no teste
8. Avaliar e interpretar erros

---

## 📊 Avaliação (o que foi analisado)
- `accuracy_score` (visão geral)
- `classification_report` (precision, recall, f1 por classe)
- `confusion_matrix` e leitura de:
  - **TN** (acertou “não sobreviveu”)
  - **FP** (previu “sobreviveu”, mas não sobreviveu)
  - **FN** (previu “não sobreviveu”, mas sobreviveu)
  - **TP** (acertou “sobreviveu”)

**Ideia-chave:** “melhor” modelo depende do custo do erro:
- Se o foco é **não perder sobreviventes**, FN costuma ser o erro mais crítico.

---

## 🚀 Melhoria simples (comparação com baseline)
Foi feita 1 melhoria mantendo o mesmo pré-processamento, trocando o classificador, por exemplo:
- Baseline: `LogisticRegression(...)`
- Melhoria: `RandomForestClassifier(random_state=42)`

A comparação foi feita olhando:
- accuracy
- matriz de confusão
- mudança em **FP e FN** (trade-off)

---

## ✅ Entregáveis da Tarefa - link - | (Aula_02/Tarefa.md) |
- `Aula_02/A02_titanic_pipeline.ipynb`
- `Aula_02/README.md`

**No notebook:** outputs das métricas + matriz de confusão + comparação final + interpretação humana.  
**No README:** resumo do baseline, pré-processamento, melhoria, comparação FP/FN e 1 limitação do dataset.

---

## 🧠 Limitações do Titanic (discussão)
- muitos valores faltantes (principalmente `deck`)
- viés histórico presente nos dados
- variáveis importantes ausentes (contexto real do acidente)