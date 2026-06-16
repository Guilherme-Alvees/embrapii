# Projeção de Indicadores Estratégicos EMBRAPII (2027) - QUESTÃO 3

> **Desafio de Análise de Dados - Questão 03** > Repositório com o script Python focado na projeção dos principais indicadores da Embrapii para o planejamento estratégico de 2027.

---

## Objetivo
Este repositório contém a solução analítica para estimar três indicadores cruciais para o planejamento de ações da Embrapii no ano de 2027:
1. **Número de novos projetos contratados** no ano.
2. **Valor total dos projetos contratados** no ano.
3. **Número de projetos concluídos** no ano.

O relatório apresenta os resultados de forma executiva, enquanto o script anexo garante total reprodutibilidade dos dados.

---

## 🔬 Metodologia e Técnicas Estatísticas Utilizadas

Para realizar estas projeções com robustez, adotamos uma abordagem dual (Híbrida), cruzando técnicas clássicas de estatística com algoritmos modernos de Inteligência Artificial:

### 1. Modelo Aditivo (Prophet - Machine Learning)
Foi a técnica principal. O **Prophet** (algoritmo open-source desenvolvido pela Meta) foi utilizado para projetar os dados mês a mês até 2027.
* **Por que o Prophet?** Ele é especialista em Séries Temporais com forte componente sazonal. A Embrapii apresenta ciclos (como picos de contratos no fim do ano). O Prophet mapeia esses "picos", remove os ruídos e projeta uma curva suavizada.

### 2. Regressão Linear Simples (OLS) - Baseline
Utilizada para validação cruzada. Agregamos os dados anualmente (2015 a 2025/2026) e calculamos a reta de melhor ajuste (Mínimos Quadrados Ordinários). 
* **Por que Regressão Linear?** É uma técnica transparente, de alta explicabilidade e perfeita para modelar a tendência macroeconômica de longo prazo.

> **Importante:** Modelos baseados em Árvores de Decisão (como Random Forest ou XGBoost) foram propositalmente descartados, pois eles não conseguem extrapolar tendências de crescimento acima do limite já treinado (o que mascararia o crescimento natural da Embrapii).

---

## Resultados da Projeção para 2027

Os resultados gerados pelo algoritmo indicam um cenário de crescimento sólido para a Embrapii. Abaixo estão as estimativas centrais projetadas para o final de 2027:

| Indicador | Expectativa Projetada (Estimativa Central) |
| :--- | :--- |
| **Novos Projetos Contratados** | Crescimento contínuo acompanhando a taxa média da série histórica, atingindo novos recordes de prospecção. |
| **Valor Total Contratado (R$)** | Salto proporcional ao ticket médio dos últimos 3 anos corrigido pela curva de tendência. |
| **Projetos Concluídos** | Aumento na cadência de entregas, reflexo direto dos picos de contratação ocorridos entre 2023 e 2025. |

*(Para visualizar os números exatos e os gráficos, clone o repositório e execute a Célula 4 do Jupyter Notebook).*

---

## Limites de Confiança (Intervalos Preditivos)

Em vez de fornecer um "número cravado" que fatalmente erraria por pequenas variações diárias, nossa inteligência artificial calculou um **Intervalo de Confiança de 90%**:
* **Limite Inferior (Cenário Conservador):** Assume pequenos atrasos ou retração macroeconômica. Há menos de 5% de chance da Embrapii perfomar abaixo dessa linha.
* **Limite Superior (Cenário Otimista):** Assume alta captação. Há menos de 5% de chance de exceder essa linha.

Do ponto de vista gerencial, o Diretor-Presidente pode planejar o orçamento baseando-se no limite inferior (segurança) e estruturar as Unidades Embrapii para o limite superior (escalabilidade).

---

## Possíveis Vieses e Limitações do Modelo

Nenhuma previsão estatística é perfeita. O modelo gerado apresenta as seguintes ressalvas interpretativas:

1. **Viés de Continuidade de Fomento:** O algoritmo matemático é cego ao ambiente político. Ele presume que os incentivos governamentais e a disponibilidade de crédito do BNDES/FINEP se manterão nos mesmos ritmos históricos.
2. **Ignora o "Teto de Vidro" (Capacidade Instalada):** O modelo projeta crescimento exponencial da demanda das empresas, mas não calcula se as atuais Unidades Embrapii possuem pesquisadores e laboratórios suficientes para absorver essa demanda em 2027.
3. **Eventos do tipo "Cisne Negro":** Pandemias, mudanças bruscas na taxa Selic ou no câmbio industrial afetam a disposição das empresas em inovar. O modelo não precifica choques não observados previamente.

---

## Reprodutibilidade (Como executar)

Este projeto foi construído seguindo os preceitos do *Zen of Python*: "Simples é melhor que complexo". 
Para que qualquer analista da Embrapii possa replicar os achados:

1. Clone este repositório.
2. Instale as dependências executando: `pip install pandas matplotlib prophet statsmodels`
3. Certifique-se de que o arquivo de dados original da Embrapii esteja no mesmo diretório.
4. Execute o notebook sequencialmente.

O código foi dividido em células modulares, livre de comentários excessivos na lógica limpa, com forte tratamento de erros (`try/except`) para garantir que falhas em arquivos locais não quebrem a aplicação inteira.