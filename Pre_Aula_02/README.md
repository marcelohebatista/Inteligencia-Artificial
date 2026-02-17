# Pré-Aula 02 — CSV + Estatística básica 

Nesta pré-aula você vai praticar o ritual essencial de análise de dados:
**carregar um CSV → checar o básico → calcular estatísticas → interpretar corretamente (sem inventar causalidade)**.

---

## 🎯 Objetivo (o que você deve conseguir fazer ao final)
Você deve conseguir:

- abrir o notebook no **Open in Colab** (botão direito → abrir em nova guia)
- salvar uma **cópia no seu Google Drive** (trabalhar sempre na sua cópia)
- gerar e carregar um CSV sintético
- calcular **média, mediana, desvio padrão**
- calcular e interpretar **correlação** (sem confundir com causa)
- criar 1 tabela resumo com **groupby**
- gerar **2 gráficos** e descrever de forma objetiva
- baixar o `.ipynb` final e publicar no GitHub (commit)

---

## 📌 Arquivo desta atividade
| **Notebook** | **Nome** | **Abrir no Colab** |
|---|---|---|
| Pré-Aula 02 | `Pre_Aula_02.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/marcelohebatista/Inteligencia-Artificial/blob/main/Pre_Aula_02/Pre_Aula_02.ipynb) |

---

## ✅ Entrega (o que você precisa enviar)
No seu repositório, envie:

- o arquivo final **`Pre_Aula_02.ipynb`**
- dentro da pasta: **`Pre_Aula_02/`**

> **Regra de ouro:** correlação **não** prova causalidade.

---

## 🧪 Checklist final (antes de entregar)
- [ ] Trabalhei na **minha cópia** (salva no Drive)
- [ ] Rodei o notebook do topo ao fim (sem células “quebradas”)
- [ ] Preenchi as respostas em português nas células de texto
- [ ] Tenho 1 tabela resumo (groupby/pivot)
- [ ] Fiz 2 gráficos (scatter + boxplot/heatmap) com interpretação objetiva
- [ ] Baixei o `.ipynb` final
- [ ] Subi no GitHub na pasta `Pre_Aula_02/` e fiz commit

---

## 🧠 O que responder (resumo das atividades)
No notebook, você deve entregar respostas para:

- **B1)** Carregamento: mostrar `df.head(5)`
- **B2)** Tamanho: `df.shape`
- **B3)** Colunas: escrever 5 colunas do dataset
- **B4)** Medidas: média, mediana e desvio padrão de `final_score`
- **B5)** Correlação: `study_hours` vs `final_score` + interpretação correta (sem causalidade)
- **B6)** Groupby: tabela resumo por `gender` (ou outra coluna categórica)
- **B7)** Gráficos: 2 gráficos + leitura objetiva
- **B8)** Conclusão (1 frase): “Neste dataset, eu observei que ____ (sem afirmar causalidade).”

---

## 🧯 Problemas comuns (e como resolver)

### “Rodei no Colab, mas não aparece no GitHub”
Colab e GitHub são coisas diferentes.  
**Solução:** baixe o `.ipynb` e faça upload no seu repositório + commit.

### “Perdi alterações”
Geralmente você não trabalhou na cópia do Drive.  
**Solução:** no começo: **Arquivo → Salvar uma cópia no Drive**.

### “Meu CSV não carrega pelo link do GitHub”
Quase sempre o link não é **raw**.  
**Solução:** use o link raw do arquivo `.csv` (ou use o dataset sintético do notebook como fallback).

### “Escrevi ‘X causa Y’ por causa da correlação”
Isso é o erro clássico (e perigoso).  
**Solução:** escreva assim:
- “há associação positiva/negativa…”
- “isso sugere uma relação linear…”
- “não é possível concluir causalidade sem experimento/controle de variáveis”

---

## ✅ Resultado esperado
Quando você terminar a Pré-Aula 02, você estará pronto para:
**ler um CSV como gente grande, tirar estatística básica e escrever conclusões honestas**.
