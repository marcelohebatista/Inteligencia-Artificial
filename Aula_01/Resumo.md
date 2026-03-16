# Aula 01 — IA aplicada + Hello Modelo (Iris)

## Teoria
- **IA aplicada** = resolver problema real com **dados + métricas**
- **Modelo** = função parametrizada que generaliza padrões
- **Treino** ajusta parâmetros para reduzir erros
- **Teste** mede generalização em dados não vistos
- **Pipeline** evita bagunça e aumenta reprodutibilidade

---

## ⚙️ Como alterar o tipo de ambiente de execução (CPU/GPU/TPU) no Google Colab
- O Colab pode iniciar em **CPU** por padrão.
- Para trocar:
  1. **Ambiente de execução (Runtime)**
  2. **Alterar tipo de ambiente de execução**
  3. Em **Acelerador de hardware**, selecione: **CPU / GPU / TPU**
  4. Clique em **Salvar**

> Observação: ao trocar CPU ↔ GPU ↔ TPU, o Colab pode reiniciar o runtime (variáveis na memória são apagadas).

---

## 🖥️ Configuração do ambiente (CPU vs GPU)
- Se você estiver em **GPU NVIDIA**, o comando `nvidia-smi` funciona.
- Se estiver em **CPU**, `nvidia-smi` pode não existir e dar erro — isso é normal.

---

## 📚 Bibliotecas que vamos usar
- **Pandas**: “Excel do Python” (tabelas e manipulação de dados)
- **Seaborn**: datasets prontos + visualizações
- **Scikit-Learn**: ML clássico (split, modelos, métricas, pipelines)

---

## 🌸 Dataset Iris (o “Hello World” da IA)
Vamos trabalhar com 3 espécies:
- **Setosa**
- **Versicolor**
- **Virginica**

### Ideia do problema
- **X (features)**: medidas da flor (sépalas e pétalas)
- **y (target)**: espécie da flor

---

## ✅ Exercício A e B
### Exercício A (EDA + entendimento do dataset)
- Carregar o Iris
- Inspecionar as primeiras linhas (`head`)
- Ver dimensões (`shape`)
- Ver estatísticas básicas (`describe`)
- Contar classes (`value_counts`)

### Exercício B (treino/teste + baseline)
- Separar `X` e `y`
- Fazer `train_test_split`
- Treinar um modelo baseline
- Avaliar com uma métrica (ex.: acurácia)
- Analisar o impacto de `random_state` e `test_size`

---

## 🧠 Por que a acurácia mudou quando alterei `random_state` (e por que `test_size` às vezes não muda)?
- `random_state` controla **como os dados são embaralhados** no split → muda quais exemplos vão para treino e teste.
- Em bases pequenas, isso pode gerar um teste:
  - mais fácil (acurácia alta)
  - mais difícil (acurácia menor)
- `test_size` muda:
  - quanto o modelo aprende (treino)
  - quanto você usa para avaliar (teste)
- No Iris, pode parecer que `test_size` “não muda nada” porque o dataset é **bem separável** e alguns splits continuam fáceis.

**Lição:** acurácia de um único split é frágil → validação cruzada é mais confiável.

---

## 👀 Por que 100% de acurácia (quase sempre) não é “bom” — é suspeito
### Principais motivos
1. **Você avaliou no lugar errado**
   - medir no treino (overfitting) pode dar 100%
2. **Split “sortudo”**
   - um teste fácil pode inflar o resultado
3. **Vazamento de dados (data leakage)**
   - pré-processar antes do split, usar informação do “futuro”, etc.
4. **Métrica inadequada**
   - acurácia pode enganar em dados desbalanceados ou quando FN/FP têm custos diferentes
5. **Às vezes é real (problema simples)**
   - mas ainda precisa de prova: CV, diferença treino vs teste, dados novos

**Mensagem final:** em ML, 100% não é troféu — é checklist.