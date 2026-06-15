# 📊 Inteligência de Negócios para E-Commerce: Segmentação RFM e Curva ABC

Desenvolvimento de uma solução analítica ponta a ponta para um e-commerce de departamentos. O projeto integra engenharia de dados, modelagem estatística/comercial e storytelling visual para transformar dados transacionais brutos em estratégias acionáveis de marketing, retenção de clientes e otimização de estoque.

---

## 🎯 Desafio de Negócio (Demanda Simulada)

A diretoria executiva de um e-commerce de varejo identificou flutuações na receita e uma necessidade urgente de aumentar a retenção de clientes e o *Lifetime Value* (LTV). Sem uma segmentação clara, as campanhas de marketing eram generalistas, gerando alto custo de desconto para clientes que já comprariam e deixando compradores de alto valor entrarem em *churn*.

**Objetivos do Projeto:**
1. **Segmentação de Clientes (RFM):** Mapear o comportamento dos consumidores com base em Recência, Frequência e Valor Monetário.
2. **Análise de Pareto (ABC) Dupla:** Identificar os clientes que concentram o faturamento e os produtos críticos da operação para otimização de estoque.

---

## 🛠️ Tecnologias e Ferramentas Utilizadas

* **Python (Pandas, NumPy):** Utilizado no ecossistema Google Colab para toda a etapa de extração, limpeza, tratamento e engenharia de recursos (regras de negócio RFM e ABC).
* **Power BI:** Construção do modelo de dados estelar, criação de medidas em DAX avançado e desenvolvimento do ecossistema de dashboards interativos.

---

## 🏗️ Desenvolvimento Técnico & Regras de Negócio

### 1. Limpeza e Tratamento de Dados (Python)
O pipeline executado no Jupyter Notebook realizou os seguintes tratamentos críticos:
* **Remoção de Cancelamentos:** Identificação e exclusão de faturas canceladas (códigos iniciados com "C" na coluna `InvoiceNo`), eliminando viés negativo no faturamento.
* **Tratamento de Nulos:** Eliminação de registros sem identificação do cliente (`CustomerID`), garantindo a integridade da análise de CRM.
* **Conversão de Tipos:** Ajuste de strings para formatos de data nativos (`datetime64`) e IDs para valores inteiros.

### 2. Engenharia de Recursos & Lógicas de Negócio
* **Cálculo RFM:** Agrupamento por cliente para extrair a data da última compra, contagem única de invoices e soma do valor total gasto. A recência foi calculada baseando-se em uma data de estudo fixa de mercado (`30/12/2011`).
* **Distribuição por Quintis:** Divisão dos scores de 1 a 5 utilizando técnicas estatísticas de quartis/quintis (`pd.qcut`) para garantir distorções controladas na base.
* **Lógica dos Segmentos:**
  * `VIPs`: Clientes ativos com excelente frequência.
  * `Potenciais / Novos`: Compras recentes, mas histórico curto.
  * `Em Risco`: Clientes de alta frequência que pararam de comprar.
  * `Inativos / Perdidos`: Clientes sem compras há muito tempo.
* **Curva ABC (Clientes e Produtos):** Ordenação decrescente de faturamento e cálculo do percentual acumulado (`.cumsum()`), aplicando as faixas clássicas de Pareto: **Classe A** (até 80% do valor), **Classe B** (80% a 95%) e **Classe C** (95% a 100%).

---

## 📊 O Dashboard Interativo

O layout foi desenvolvido priorizando a experiência do usuário (*UX*) e a rapidez na tomada de decisão gerencial, dividindo-se em três visões principais:
1. **Visão de Vendas Geral:** KPIs macro (Faturamento, Ticket Médio, Peças Vendidas) e distribuição temporal e geográfica.
2. **Análise de Clientes (Matriz Cruzada):** O coração do CRM, cruzando os blocos RFM com as classes ABC em formato matricial.
3. **Análise de Produtos:** Concentração de receita do catálogo e identificação de itens críticos da Curva ABC.

---

## 📈 Principais Insights de Negócio

* **Hiperconcentração de Receita (Pareto Extremo):** Apenas **26% dos clientes** cadastrados (Classe A) representam **80% de todo o faturamento** do e-commerce ($7,12M de um total de $8,91M).
* **Alerta Crítico de Churn:** Identificou-se um grupo de **1.866 clientes "Em Risco"** que pertencem à **Classe A**, acumulando mais de **$1,09 milhão de faturamento histórico paralisado**.
* **Sazonalidade e Ruptura:** O faturamento apresenta um pico expressivo em Novembro ($1,16M) e sofre queda de mais de 50% em Dezembro ($0,52M). O cruzamento de dados sugere potencial esgotamento (*stockout*) dos produtos Classe A (como o líder *Paper Craft, Little Birdie*, que faturou sozinho $168k) após o evento de Black Friday.

---

## 🔗 Acesso ao Projeto

* 💻 **Código Fonte:** [Acesse o Notebook Tratado](https://colab.research.google.com/drive/1qbsxbDr-Fxm8fUO-O_KPRf7e8pgle_HZ?usp=sharing)
* 💼 **Acompanhamento de Negócios:** [Veja a documentação detalhada deste portfólio no meu Notion](https://app.notion.com/p/Carlos-Portf-lio-Projetos-em-Dados-Data-Science-Analysis-37f1ee6b3a06805caa59e989636a8c90?source=copy_link)

---
Desvolvido por **Carlos** — [LinkedIn](https://www.linkedin.com/in/carlos-vital-junior-429138122/) | [GitHub]((https://github.com/cvitaljr))
