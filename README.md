# MVP – Análise de Obesidade com Arquitetura Lakehouse (Bronze / Silver / Gold)

Este repositório contém o notebook desenvolvido para o **MVP da disciplina**, cujo objetivo é realizar uma análise exploratória e analítica sobre fatores associados à obesidade, utilizando uma arquitetura de dados em camadas (**Bronze, Silver e Gold**) e consultas SQL/Spark, complementadas por visualizações em Python.

---

## 🎯 Objetivo do Projeto

Analisar como **fatores clínicos, familiares e comportamentais** se relacionam com os diferentes níveis de obesidade, respondendo hipóteses definidas previamente por meio de indicadores agregados e visualizações analíticas.

O foco do trabalho está em:
- Organização correta dos dados em camadas
- Análise de qualidade de dados
- Construção de métricas analíticas
- Discussão e interpretação dos resultados (Item 5 do MVP)

---

## 📥 Coleta dos Dados

O conjunto de dados utilizado no projeto é **público** e foi obtido a partir de uma fonte aberta (Kaggle), contendo informações **sintéticas e previamente curadas** relacionadas a características demográficas, clínicas e comportamentais associadas à obesidade.  

Os dados são baixados programaticamente no notebook e persistidos na plataforma **Databricks**, compondo a **camada Bronze** do pipeline, garantindo reprodutibilidade do processo de coleta e rastreabilidade dos dados desde sua origem.

---

## 🏗️ Arquitetura de Dados (Lakehouse)

O projeto segue o padrão **Bronze → Silver → Gold**, adotando boas práticas de organização e tratamento de dados.

### 🥉 Camada Bronze
- Dados brutos obtidos via download do dataset
- Nenhuma transformação estrutural
- Análise inicial de qualidade:
  - Valores nulos
  - Duplicatas
  - Faixas plausíveis (idade, altura, peso)

### 🥈 Camada Silver
- Limpeza e padronização:
  - Padronização dos nomes das colunas
  - Remoção de duplicatas
- Criação de variáveis derivadas:
  - **IMC (BMI)**
  - Codificação numérica de variáveis ordinais (**CAEC** e **CALC**)
- Garantia de dados consistentes e prontos para análise

### 🥇 Camada Gold
- Dados agregados por classe de obesidade (`nobeyesdad`)
- Métricas analíticas utilizadas para responder às hipóteses:
  - IMC médio
  - Proporção de histórico familiar
  - Proporção de consumo de alimentos calóricos (FAVC)
  - Desvio em relação à média global
  - Score de risco agregado

---

## 📚 Catálogo de Dados

O catálogo de dados do MVP é documentado de forma **conceitual e funcional** no notebook principal, a partir da descrição das camadas Bronze, Silver e Gold, bem como do significado e finalidade dos principais atributos utilizados em cada etapa do pipeline.

O catálogo inclui:
- Descrição das tabelas por camada
- Granularidade dos dados
- Regras de transformação aplicadas
- Dicionário de dados em nível de colunas
- **Modelo gráfico das tabelas**, representando o fluxo Bronze → Silver → Gold

Essa documentação garante compreensão, rastreabilidade e reprodutibilidade das análises realizadas.

---

## 🧩 Modelo de Dados

O modelo de dados segue uma arquitetura Lakehouse em três camadas (Bronze, Silver e Gold), representada por um **diagrama gráfico** que ilustra a evolução dos dados desde sua forma bruta até sua consolidação analítica.  

O diagrama encontra-se documentado no notebook do projeto e evidencia as transformações aplicadas em cada camada.

---

## 🔬 Hipóteses Analisadas

O trabalho avalia as seguintes hipóteses:

- **H1:** Classes mais severas de obesidade apresentam maior IMC médio.
- **H2:** A proporção de indivíduos com histórico familiar de sobrepeso é maior em classes mais severas.
- **H3:** O consumo frequente de alimentos calóricos é mais comum em níveis mais elevados de obesidade.
- **H4:** Classes mais severas apresentam IMC médio acima da média global da população.
- **H5:** A combinação de fatores clínicos, familiares e comportamentais resulta em maior risco agregado de obesidade.

Cada hipótese é avaliada por:
- Consulta SQL na camada Gold
- Visualização gráfica
- Interpretação analítica
- Discussão das limitações
- Conclusão explícita sobre o suporte à hipótese

---

## 📊 Visualizações

Para cada hipótese, foram gerados gráficos utilizando **Python (Pandas + Matplotlib)**, a partir dos resultados das consultas Spark SQL, incluindo:

- Gráfico de barras de IMC médio (H1)
- Gráfico de proporção de histórico familiar (H2)
- Gráfico de consumo de alimentos calóricos – FAVC (H3)
- Gráfico de desvio do IMC em relação à média global (H4)
- Gráfico de score de risco agregado (H5)

As visualizações reforçam visualmente as evidências discutidas no texto analítico.

---

## 🧠 Discussão dos Resultados

O notebook contém:
- Análise detalhada de cada hipótese (Item 5b)
- Discussão final consolidada, abordando:
  - Suporte às hipóteses H1–H5
  - Impacto amostral das classes
  - Tendências comportamentais e familiares
  - Limitações do estudo

---

## ⚠️ Limitações

- O conjunto de dados utilizado é **sintético e previamente curado**
- A análise é **descritiva**, não permitindo inferência causal
- Variáveis socioeconômicas e outros fatores contextuais não estão disponíveis
- O score de risco agregado utiliza pesos heurísticos, não estatísticos

Apesar dessas limitações, o trabalho atende plenamente aos objetivos do MVP, demonstrando a capacidade do modelo de dados e das análises em responder às perguntas propostas.

---

## 🛠️ Tecnologias Utilizadas

- Databricks
- Apache Spark (Spark SQL)
- Python
- Pandas
- Matplotlib
- Delta Lake

---

## 📁 Conteúdo do Repositório

- `All Code - MVP aligned (...).ipynb` – Notebook principal com todo o pipeline, análises e diagramas
- `README.md` – Este arquivo

---

## ✅ Status do Projeto

✔️ MVP completo  
✔️ Item 5a (Qualidade de dados) atendido  
✔️ Item 5b (Solução do problema) atendido  
✔️ Catálogo de dados e modelo gráfico documentados  
✔️ Pronto para entrega / avaliação  

---

## 👤 Autor

Projeto desenvolvido como parte do MVP da disciplina de Banco de Dados / Data Warehouse.
