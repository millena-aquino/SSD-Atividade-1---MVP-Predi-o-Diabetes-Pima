# MVP — Predição de Diabetes em Pacientes Pima

**Disciplina:** Sistemas de Suporte a Decisão — Universidade de Brasília
**Professor:** Prof. Dr. André Luiz Marques Serrano
**Base:** *Pima Indians Diabetes Database* (768 pacientes, 8 variáveis clínicas + alvo)

## Conteúdo

- `MVP_Predicao_Diabetes_Pima.ipynb` — notebook completo
- `pima.csv` — base de dados usada (sem cabeçalho; colunas nomeadas dentro do notebook).

## Estrutura do notebook

1. Descrição do problema
2. Sobre o dataset
3. Hipóteses e premissas
4. Metodologia (CRISP-DM, split 64/16/20 estratificado)
5. **Limpeza dos dados** — o achado central: a base não tem `NaN` explícito, mas cinco variáveis clínicas (glicose, pressão, espessura de pele, insulina, IMC) registram zero onde zero é fisiologicamente impossível. Tratamento: zero → ausente → imputação por mediana estratificada por classe + indicadores de ausência para as duas variáveis mais afetadas.
6. Análise exploratória (univariada, bivariada, correlação)
7. Pré-processamento (split, imputação ajustada só no treino, padronização)
8. Modelagem preditiva (baseline, Regressão Logística, KNN, Árvore, Random Forest, SVM; validação cruzada 5-fold; `GridSearchCV` no modelo líder)
9. Avaliação final no teste (matriz de confusão, curva ROC, métricas)
10. Importância das variáveis
11. Conclusões e verificação das hipóteses
12. Limitações
13. Referências

## Resultado principal

Random Forest (ajustado por `GridSearchCV`) — **AUC-ROC ≈ 0,95** no conjunto de teste, com `Glucose` como variável mais importante, confirmando a hipótese de que a glicemia plasmática é o sinal clínico mais direto de diabetes nesta base.

## Como executar

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
jupyter notebook MVP_Predicao_Diabetes_Pima.ipynb
```

Reprodutibilidade garantida por `RANDOM_STATE = 42` em todos os componentes estocásticos.
