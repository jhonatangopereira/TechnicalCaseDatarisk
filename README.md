# Modelo de Predição de Inadimplência - Datarisk Technical Case

## 📋 Descrição do Projeto

Este projeto implementa um modelo de Machine Learning para prever a probabilidade de inadimplência de clientes, baseado na análise de dados históricos de pagamentos. A inadimplência é definida como pagamentos realizados com 5 ou mais dias de atraso em relação à data de vencimento.

## 🎯 Objetivos

- **Análise Exploratória**: Compreender as características dos dados e identificar padrões de inadimplência
- **Engenharia de Features**: Criar variáveis relevantes para o modelo
- **Modelagem**: Desenvolver modelos de Machine Learning para predição de inadimplência
- **Avaliação**: Comparar diferentes algoritmos e selecionar o melhor modelo
- **Predição**: Aplicar o modelo nos dados de teste para gerar probabilidades de inadimplência

## 📊 Estrutura dos Dados

### Bases de Dados

1. **`base_cadastral.csv`**: Dados cadastrais dos clientes
   - ID_CLIENTE, DATA_CADASTRO, DDD, FLAG_PF, SEGMENTO_INDUSTRIAL, DOMINIO_EMAIL, PORTE, CEP_2_DIG

2. **`base_info.csv`**: Informações mensais dos clientes
   - ID_CLIENTE, SAFRA_REF, RENDA_MES_ANTERIOR, NO_FUNCIONARIOS

3. **`base_pagamentos_desenvolvimento.csv`**: Histórico de cobranças e pagamentos (dados de treino)
   - ID_CLIENTE, SAFRA_REF, DATA_EMISSAO_DOCUMENTO, DATA_PAGAMENTO, DATA_VENCIMENTO, VALOR_A_PAGAR, TAXA

4. **`base_pagamentos_teste.csv`**: Cobranças recentes para predição
   - ID_CLIENTE, SAFRA_REF, DATA_EMISSAO_DOCUMENTO, DATA_VENCIMENTO, VALOR_A_PAGAR, TAXA

## 🛠️ Tecnologias Utilizadas

- **Python 3.x**
- **Pandas**: Manipulação e análise de dados
- **NumPy**: Computação numérica
- **Scikit-learn**: Machine Learning
- **Matplotlib/Seaborn**: Visualização de dados
- **Jupyter Notebook**: Ambiente de desenvolvimento

## 📁 Estrutura do Projeto

```
TechnicalCaseDatarisk/
├── data/
│   ├── base_cadastral.csv
│   ├── base_info.csv
│   ├── base_pagamentos_desenvolvimento.csv
│   ├── base_pagamentos_teste.csv
│   └── resultados_predicao_inadimplencia.csv (gerado)
├── data-analysis.ipynb
└── README.md
```

## 🚀 Como Executar

### Pré-requisitos

```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
```

### Execução

1. Abra o Jupyter Notebook:
```bash
jupyter notebook
```

2. Execute o arquivo `analise_regressao_dias_atraso.ipynb` célula por célula

3. Os resultados serão salvos automaticamente em `./data/resultados_predicao_inadimplencia.csv`

## 📈 Metodologia

### 1. Análise Exploratória
- Caracterização das bases de dados
- Análise de missing values
- Distribuição das variáveis
- Correlações entre features

### 2. Engenharia de Features
- **Features Temporais**: Mês, ano e dia da semana de pagamento
- **Features de Valor**: Categorização por faixas de valor
- **Features de Taxa**: Categorização por faixas de taxa
- **Merge de Dados**: Integração das bases cadastral e de informações mensais

### 3. Preparação dos Dados
- Tratamento de missing values (imputação)
- Encoding de variáveis categóricas
- Normalização de features numéricas

### 4. Modelagem
- **Random Forest**: Modelo ensemble robusto
- **Logistic Regression**: Modelo linear interpretável
- **Avaliação**: ROC AUC, Classification Report, Matriz de Confusão

### 5. Predição
- Aplicação do melhor modelo nos dados de teste
- Geração de probabilidades de inadimplência
- Categorização por níveis de risco (Baixo, Médio, Alto)

## 📊 Resultados

O modelo gera as seguintes saídas:

1. **PROBABILIDADE_INADIMPLENCIA**: Probabilidade estimada (0-1)
2. **RISCO_INADIMPLENCIA**: Categoria de risco (Baixo, Médio, Alto)

### Categorias de Risco
- **Baixo**: Probabilidade < 30%
- **Médio**: Probabilidade entre 30% e 70%
- **Alto**: Probabilidade > 70%

## 🔍 Análises Incluídas

- Distribuição da variável target
- Correlação entre features
- Taxa de inadimplência por segmento industrial
- Taxa de inadimplência por porte da empresa
- Importância das features (Random Forest)
- Comparação de modelos (ROC AUC)
- Análise dos resultados de predição

## 📝 Outputs

### Arquivo de Resultados
O arquivo `resultados_predicao_inadimplencia.csv` contém:
- Todos os dados originais dos pagamentos de teste
- Probabilidade de inadimplência para cada registro
- Categoria de risco associada

### Visualizações
- Gráficos de distribuição da variável target
- Matriz de correlação
- Análise por segmento e porte
- Curvas ROC dos modelos
- Importância das features
- Distribuição das probabilidades de predição

## 🎯 Aplicações Práticas

Este modelo pode ser utilizado para:

1. **Gestão de Risco**: Identificar clientes com alto risco de inadimplência
2. **Decisões de Crédito**: Ajustar políticas de concessão de crédito
3. **Cobrança Proativa**: Priorizar ações de cobrança
4. **Pricing**: Ajustar taxas baseado no risco
5. **Monitoramento**: Acompanhar tendências de inadimplência

---

**Nota**: Este projeto foi desenvolvido como parte do Technical Case da Datarisk, focando na aplicação prática de Machine Learning para predição de inadimplência. 