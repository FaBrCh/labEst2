### 1. Diagnóstico do Problema

A análise de resíduos dos modelos de regressão linear (`modelo_stepwise_refinado` e `modelo_hierarquico_refinado`) revelou uma violação do pressuposto de **normalidade dos resíduos**. Ambos os testes de Shapiro-Wilk apresentaram um p-valor < 0.05, indicando que os resíduos não seguem uma distribuição normal.

A causa raiz é a natureza da variável dependente, `pedsqlglobal36`, que é um escore limitado (0-100) com um forte "efeito teto" (valores concentrados próximos de 100). Modelos de regressão linear padrão não são ideais para esse tipo de dado.

### 2. Estratégia de Modelagem Avançada

Para resolver essa questão, propõe-se a utilização de Modelos Lineares Generalizados (GLMs) que são mais adequados à distribuição dos dados.

#### Opção A: Regressão Beta (Recomendada)

-   **O que é?** Um modelo projetado para variáveis contínuas que representam proporções ou taxas, ou seja, que são limitadas a um intervalo (0, 1).
-   **Por que usar?** É a abordagem teoricamente mais sólida para a nossa variável resposta. Ao reescalar o escore PEDSQL para o intervalo (0, 1), podemos modelar sua média de forma robusta, respeitando suas características de assimetria e limites.
-   **Plano de Ação:**
    1.  **Transformar a variável resposta:** Converter `pedsqlglobal36` da escala [0, 100] para (0, 1). É preciso verificar se existem valores exatamente iguais a 0 ou 100, pois a regressão beta padrão não os aceita. Se existirem, uma pequena correção será necessária.
    2.  **Ajustar o modelo:** Usar o pacote `betareg` em R para ajustar o modelo. Podemos usar as mesmas variáveis do nosso melhor modelo anterior (o `modelo_stepwise_refinado`).
    3.  **Analisar os resultados:** Interpretar os coeficientes e avaliar a qualidade do ajuste do novo modelo.

#### Opção B: Regressão Quantílica (Alternativa)

-   **O que é?** Um modelo que, em vez de focar na média, modela a mediana (ou outros quantis) da variável resposta.
-   **Por que usar?** Não faz nenhuma suposição sobre a distribuição dos resíduos, tornando-se uma alternativa muito robusta. É especialmente útil quando a relação entre as variáveis pode ser diferente para crianças com baixa vs. alta qualidade de vida.
-   **Plano de Ação:**
    1.  **Ajustar o modelo:** Usar o pacote `quantreg` em R para ajustar o modelo para a mediana (tau = 0.5).
    2.  **Analisar os resultados:** Interpretar como as variáveis se associam com a mediana da qualidade de vida.

### 3. Decisão

A estratégia será:

1.  **Implementar a Regressão Beta** como primeira abordagem.
2.  Avaliar seus resultados e diagnósticos.
3.  Se a Regressão Beta se mostrar inadequada por algum motivo, proceder com a **Regressão Quantílica**.
4.  O modelo final será aquele que for estatisticamente válido e oferecer a interpretação mais clara e útil para os objetivos da pesquisa. 