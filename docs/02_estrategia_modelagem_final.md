# Plano de Ação: Modelagem Final e Validação

Este documento descreve os próximos passos para a análise de regressão, incorporando o feedback da reunião e a sugestão da orientadora para uma abordagem de modelagem mais robusta.

## 1. Reestruturação da Estratégia de Modelagem

A abordagem anterior será substituída por um **Modelo Hierárquico Sequencial**, conforme a sugestão da orientadora. Esta metodologia constrói o modelo em etapas, adicionando blocos de variáveis em uma ordem teórica pré-definida.

### Novo Modelo: "Modelo Hierárquico Sequencial"

O objetivo é entender como a contribuição de certas variáveis se sustenta após a inclusão de novos grupos de fatores.

**Passos:**

1.  **Definição dos Blocos:** Manter a descrição clara dos blocos no relatório.
    -   **Bloco 1:** Saúde Perinatal
    -   **Bloco 2:** Contexto Social
    -   **Bloco 3:** Hábitos de Tela
    -   **Bloco 4:** Desenvolvimento

2.  **Construção Sequencial:** O processo será transparente no relatório, mostrando cada passo.
    -   **Modelo 1:** Ajustar `pedsqlglobal36 ~ genero + [Bloco 1]`.
    -   **Seleção 1:** Identificar as variáveis significativas (p < 0.05) do Modelo 1.
    -   **Modelo 2:** Ajustar `pedsqlglobal36 ~ genero + [Variáveis Sig. da Seleção 1] + [Bloco 2]`.
    -   **Seleção 2:** Identificar as variáveis significativas (p < 0.05) do Modelo 2.
    -   **Modelo 3:** Ajustar `pedsqlglobal36 ~ genero + [Variáveis Sig. da Seleção 2] + [Bloco 3]`.
    -   **Seleção 3:** Identificar as variáveis significativas (p < 0.05) do Modelo 3.
    -   **Modelo Final:** Ajustar `pedsqlglobal36 ~ genero + [Variáveis Sig. da Seleção 3] + [Bloco 4]`. Este será o `modelo_hierarquico_final`.

3.  **Limpeza do Relatório:** As seções de modelagem anteriores que não seguem esta lógica serão removidas ou substituídas.

## 2. Análise de Resíduos

A análise de resíduos será mantida, mas agora focará nos dois modelos finalistas:
1.  `modelo_stepwise_refinado`: O melhor modelo segundo os critérios puramente estatísticos.
2.  `modelo_hierarquico_final`: O novo modelo construído pela metodologia sequencial.

**Análises a serem feitas para cada modelo:**
-   Gráfico de Resíduos vs. Ajustados (Linearidade e Homocedasticidade).
-   Gráfico Q-Q Normal (Normalidade dos Resíduos).
-   Gráfico Scale-Location (Homocedasticidade).

## 3. Comparação Final e Discussão

A tabela de comparação de modelos será atualizada para incluir o novo `Modelo Final Teórico`. A seção de discussão será preenchida para comparar os méritos das duas abordagens finalistas (a puramente estatística do `stepwise` e a teórica da seleção por blocos), auxiliando na escolha do modelo definitivo para o relatório. 