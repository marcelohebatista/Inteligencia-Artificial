# Disciplina: Inteligência Artificial
## Aula 01 — IA aplicada + Hello Model (Iris)
**Professor:** Marcelo Batista

---

# 🎯 Objetivos da aula
1. Entender o ambiente do Google Colab (CPU/GPU)
2. Manipular dados com Pandas (dataset Iris)
3. Treinar seu primeiro modelo de ML (baseline)
4. Entender o fluxo sagrado: **Dados → Treino → Teste**
5. Aprender noções de reprodutibilidade (pipeline/boas práticas)
6. Exercícios

---

# 🧩 IA aplicada (o que é “na prática”?)
- **IA aplicada** = resolver problema real com **dados + métricas**
- **Modelo** = função parametrizada que aprende padrões
- **Treino** ajusta parâmetros para reduzir erros
- **Teste** mede generalização em dados não vistos
- **Pipeline** reduz bagunça e melhora reprodutibilidade

---

# 🖥️ Colab: CPU vs GPU (o que importa hoje)
- Colab pode iniciar em **CPU**
- Trocar CPU ↔ GPU pode **reiniciar o runtime** (variáveis somem)
- Nesta aula (Scikit-Learn / ML clássico), **GPU não é obrigatória**
- Mesmo assim, vamos **checar** (hábito profissional)

---

# 🧪 Check de GPU “à prova de erro”
**Ideia:**
- Se tiver GPU NVIDIA, `nvidia-smi` funciona
- Se não tiver, é normal dar “comando não encontrado”

**O que observar no output:**
- Nome da GPU (ex.: Tesla T4)
- Memória/uso (geralmente 0% em ML clássico)

---

# 📦 Bibliotecas que vamos usar
- **Pandas**: “Excel do Python”
- **Seaborn**: datasets prontos + visual
- **Scikit-Learn**: split, modelos, métricas

Imports principais:
- `train_test_split`
- `DecisionTreeClassifier`
- `accuracy_score`

---

# 🌸 Dataset Iris (o “Hello World” da IA)
Usaremos 3 espécies:
- Setosa
- Versicolor
- Virginica

Colunas (features):
- `sepal_length`, `sepal_width`, `petal_length`, `petal_width`

---

# 🔎 Carregando e olhando os dados
Passos:
1) `df = sns.load_dataset("iris")`
2) `df.head()` para ver a tabela
3) `df.shape` para dimensão
4) `value_counts()` para contar classes

**Checkpoint:** dataset pequeno, limpo, ótimo para aprender o fluxo.

---

# 🧠 Definição do problema (X e y)
- **X (features):** medidas da flor (sépalas/pétalas)
- **y (target):** `species` (o rótulo: setosa/versicolor/virginica)

Separação:
- `X = df.drop("species", axis=1)`
- `y = df["species"]`

---

# 📏 EDA rápido (sem virar novela)
O mínimo para não “voar cego”:
- `df.describe()` (estatística básica)
- `df["species"].value_counts()` (distribuição das classes)

O que a gente quer responder:
- Está balanceado?
- Tem valores faltantes?
- As features fazem sentido?

---

# 🛐 Fluxo sagrado: Dados → Treino → Teste
- **Treino**: onde o modelo aprende padrões
- **Teste**: onde avaliamos generalização

Frase-chave:
> Se eu avaliar no treino, posso me enganar (overfitting).

---

# 🌳 Baseline: Árvore de Decisão (DecisionTreeClassifier)
Passos:
1) `train_test_split(...)`
2) `modelo.fit(X_train, y_train)`
3) `pred = modelo.predict(X_test)`
4) `acc = accuracy_score(y_test, pred)`

Output esperado (às vezes):
- `Acurácia (Iris, split único): 1.0000`

---

# 🌍 Teste “mundo real” (1 amostra nova)
Criamos uma nova flor:
- `nova_flor = [[5.1, 3.5, 1.4, 0.2]]`

E pedimos:
- `modelo.predict(nova_flor)`

Objetivo didático:
- Ver o modelo funcionando fora do dataset (mesmo que ainda seja um exemplo simples)

---

# ⚠️ 100% de acurácia: comemorar ou desconfiar?
Por que pode acontecer no Iris:
- dataset “didático”, relativamente separável
- setosa costuma ser muito fácil de separar

Por que **pode enganar**:
- split “sortudo”
- overfitting (em outros contextos)
- vazamento de dados (em problemas reais)

Moral:
> 100% não é troféu; é checklist.

---

# 🧪 Exercício A — Entendendo os dados (Iris)
Faça:
1) Mostre:
- `df.shape`
- `df.info()`
- `df.isna().sum()`

2) Mostre:
- `df["species"].value_counts()`

3) Escreva 2 linhas:
- o que é **X** e o que é **y** no Iris

**Evidência mínima:** outputs de shape, isna().sum e value_counts.

---

# 🧪 Exercício B — Seu primeiro baseline (Iris)
Objetivo: ver como o split muda a avaliação.

1) Comparar `test_size` (mantendo `random_state=42`)
- `test_size=0.2`
- `test_size=0.3`

2) Comparar `random_state` (mantendo `test_size=0.2`)
- `random_state=42`
- `random_state=7`

**Evidência mínima:** 4 acurácias impressas.

---

Frase final:
> Avaliar bem é tão importante quanto treinar bem.

---

# 🧾 Encerramento (o que você já sabe agora)
Ao final da Aula 01 você consegue:
- Carregar e inspecionar um dataset (Iris)
- Definir X e y
- Treinar um baseline com scikit-learn
- Medir acurácia em teste
- Entender por que o split muda o resultado
- Entregar evidências mínimas dos exercícios (prints/outputs)
