# Proposta do Estudo - LabEst Rodada 2

**Título:** Risco para Perda Auditiva e suas Associações com o Desenvolvimento e a Qualidade de Vida de Crianças aos 36 Meses de Idade

**Data:** Junho de 2025  
**Laboratório:** LabEst (Laboratório de Estatística)

---

## 1. Objetivo Principal

Analisar a associação entre o **risco para perda auditiva** e o **desenvolvimento global** e **qualidade de vida** de crianças aos 36 meses de idade.

## 2. População de Estudo

- **Idade das crianças:** 36 meses
- **Fonte de dados:** Arquivo "BAYLEY TRIAGEM AUDITIVA ANÁLISE ESTATÍSTICA 16052025.xls"

## 3. Variáveis Principais

### 3.1. Variável Resposta (Outcome)
- **PEDSQL Global** (`pedsqlglobal36`): Escala de qualidade de vida 
- **PEDSQL Físico** (`pedsqlfisico36`): Componente físico da qualidade de vida
- **PEDSQL Psicossocial** (`pedsqlpsico36`): Componente psicossocial da qualidade de vida

### 3.2. Variáveis Explicativas

#### **Triagem Auditiva (Foco Principal)**
- **TANU** (`tanu`): Realização da Triagem Auditiva Neonatal Universal
- **Resultado TANU** (`resultadotanu`): Resultado da triagem neonatal
- **QTAI** (`resultqtai36`): Questionário de Triagem de Alterações Auditivas Infantil aos 36 meses

#### **Variáveis Sociodemográficas e Perinatais**
- Idade da mãe (adolescente vs. adulta)
- Peso ao nascimento (< 2500g vs. ≥ 2500g)
- Idade gestacional (< 37 sem vs. ≥ 37 sem)
- Via de parto (cesariana vs. vaginal/fórceps)
- Aleitamento materno exclusivo aos 6 meses
- Etnia (branco vs. não branco)
- Estado civil materno
- Escolaridade materna
- Classe socioeconômica (ABEP)
- Gênero da criança

#### **Desenvolvimento Infantil (Escala Bayley)**
- Desenvolvimento cognitivo
- Linguagem receptiva e expressiva
- Motricidade fina e grossa
- **Critério:** Pontuação < 85 = Atraso no desenvolvimento

#### **Hábitos e Ambiente**
- Frequência à creche
- Quantidade de atividades lúdicas
- **Uso de telas:** tempo diário, horário fixo, supervisão, limites de tempo e conteúdo

## 4. Metodologia Estatística

### 4.1. Análise Descritiva
- Frequências absolutas e relativas para variáveis categóricas
- Médias, desvios-padrão e testes de normalidade para variáveis contínuas
- Boxplots para visualização das associações

### 4.2. Análise Inferencial
- **Testes univariados:** 
  - Teste t para 2 grupos
  - ANOVA para múltiplos grupos
- **Critério de seleção:** Variáveis com p-valor < 0.25 serão incluídas no modelo multivariado
- **Modelagem:** Regressão múltipla com seleção de variáveis (stepwise ou manual)
