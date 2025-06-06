# Documentação do Pré-processamento de Dados

**Projeto:** Risco para Perda Auditiva e suas Associações com o Desenvolvimento e a Qualidade de Vida de Crianças aos 36 Meses de Idade.
**Data:** 31 de maio de 2025
**Autor:** Fabrício (via Assistente Gemini)

---

## 1. Contexto do Projeto

Este documento detalha as etapas de pré-processamento e limpeza dos dados utilizados na análise estatística do projeto. O objetivo principal da pesquisa é analisar a associação entre o risco para perda auditiva e o desenvolvimento global e qualidade de vida de crianças aos 36 meses.

A análise é realizada no ambiente R, utilizando o arquivo Quarto (`analise_descritiva.qmd`) para garantir a reprodutibilidade.

## 2. Fonte de Dados

- **Arquivo Original:** `data/BAYLEY TRIAGEM AUDITIVA ANÁLISE ESTATÍSTICA 16052025.xls`
- **Formato:** Planilha do Microsoft Excel (.xls)

## 3. Etapas de Limpeza e Preparação

O script `analise_descritiva.qmd` executa as seguintes etapas para preparar os dados brutos para a análise exploratória e modelagem.

### 3.1. Carregamento dos Dados

Os dados foram carregados para o ambiente R utilizando a função `readxl::read_xls()`.

### 3.2. Padronização dos Nomes das Variáveis

Os nomes das colunas na planilha original continham espaços, acentos e letras maiúsculas (ex: "Idade mãe cat"). Para facilitar a manipulação e evitar erros de digitação, os nomes foram padronizados para o formato `snake_case` (ex: `idademaecat`).

- **Ferramenta:** `janitor::clean_names()`

### 3.3. Remoção de Variáveis Derivadas Redundantes

O conjunto de dados original continha variáveis de pontuação bruta (ex: `cogbal36`) e as suas respectivas classificações (ex: `classcogbal36`). Para evitar redundância e focar a análise nas classificações de "Normal" vs. "Atraso", as seguintes variáveis de pontuação bruta da escala Bayley foram removidas:

- `pontosabep36`
- `somaludicas36`
- `cogbal36`
- `cogcomp36`
- `lrbal36`
- `lebal36`
- `lingcomp36`
- `mfbal36`
- `mgbal36`
- `motorcomp36`

### 3.4. Tratamento de Valores Ausentes (Missing Values)

No banco de dados original, valores ausentes foram registrados com o texto "Missing". Para que o R os reconhecesse corretamente como dados faltantes, todas as ocorrências de `"Missing"` foram substituídas por `NA` (Not Available).

- **Lógica:** `dplyr::mutate(across(everything(), ~ifelse(. == 'Missing', NA, .)))`

## 4. Estrutura Final dos Dados

Após as etapas de limpeza, o `data.frame` resultante contém as variáveis de interesse prontas para a análise, com nomes padronizados e valores ausentes corretamente codificados. Este dataset é a base para todas as análises descritivas, visualizações e modelos estatísticos subsequentes. 