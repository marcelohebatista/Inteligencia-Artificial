# 🛳️ Tarefa — Aula 02 (Titanic)

## 🎯 Objetivo
Criar um notebook (Colab/Jupyter) com o fluxo **Dados → Treino → Teste**, usando **Pipeline + ColumnTransformer**, treinando um **baseline** e fazendo **1 melhoria**, com avaliação e interpretação de erros.

---

## ✅ O que deve existir no notebook (obrigatório)

### 1) Carregar o dataset
- Usar: `sns.load_dataset("titanic")`
- Remover a coluna: `alive`
- Mostrar:
  - `head()`
  - `shape`
  - `isna().sum()` (faltantes)

### 2) Separar `X` e `y`
- `y = df_t["survived"]`
- `X = df_t.drop(columns=["survived"])`
- Imprimir `X.shape` e `y.shape`

### 3) Split (Treino/Teste)
- Usar:
  - `test_size=0.2`
  - `random_state=42`
  - `stratify=y`

### 4) Definir colunas numéricas e categóricas
- Detectar com `select_dtypes`
- Imprimir a lista de `num_cols` e `cat_cols`

### 5) Pré-processamento (Pipeline + ColumnTransformer)
- Numéricas:
  - `SimpleImputer(strategy="median")`
  - `StandardScaler()`
- Categóricas:
  - `SimpleImputer(strategy="most_frequent")`
  - `OneHotEncoder(handle_unknown="ignore")`

### 6) Baseline (Logistic Regression)
- Criar `model_baseline_lr = Pipeline([("prep", preprocess), ("clf", LogisticRegression(...))])`
- Treinar com `fit(X_train, y_train)`
- Prever com `predict(X_test)`

### 7) Avaliação do baseline
Imprimir:
- `accuracy_score`
- `classification_report`
- `confusion_matrix`
- Extrair `TN, FP, FN, TP`

### 8) 1 melhoria simples + comparação
Escolher **uma**:
- Trocar o classificador para `RandomForestClassifier(random_state=42)`
**ou**
- Ajustar o baseline para reduzir FN (ex.: `class_weight="balanced"` na LogisticRegression)

Repetir:
- treino, predição e avaliação
- comparar **accuracy + (TN, FP, FN, TP)**

### 9) Interpretação (texto em Markdown, 5–8 linhas)
Responder:
1. O modelo erra mais em qual classe (0 ou 1) e por quê (use report/matriz)?  
2. O que mudou em **FP** e **FN** do baseline para a melhoria (trade-off)?  
3. Cite 1 limitação do dataset (missing, viés histórico, variável ausente etc.)

---

## 📦 Entrega (GitHub/AVA)

### Arquivos
- `Aula_02/A02_titanic_pipeline.ipynb`
- `Aula_02/README.md`

### README.md (5 bullets)
1) Baseline escolhido (e por quê)  
2) Como tratou missing values (num e cat)  
3) Qual foi a melhoria (e por quê)  
4) O que mudou em FP e FN (comparação objetiva)  
5) Uma limitação do dataset  

---

## 🧪 Regras
- O notebook deve rodar **do zero ao fim** (Run all) sem erros.
- Usar `random_state=42` onde couber.
- Não fazer pré-processamento fora do Pipeline (evitar leakage).