# Tech Challenge Fase 1 - Case NPS Preditivo

## Objetivo do projeto

Este projeto foi desenvolvido como parte do Tech Challenge da Fase 1 da Pós Tech em AI Scientist da FIAP. O objetivo é analisar quais fatores operacionais mais influenciam a satisfação do cliente em um e-commerce e avaliar como dados históricos podem apoiar uma atuação mais proativa antes da aplicação da pesquisa de NPS.

Além da análise exploratória, o projeto também propõe uma abordagem preditiva para classificar clientes em categorias de satisfação, buscando identificar sinais de risco de insatisfação ao longo da jornada.

## Problema de negócio

Atualmente, o NPS é coletado apenas ao final da jornada de compra, o que limita a capacidade da empresa de agir preventivamente. Nesse contexto, o projeto busca responder à seguinte pergunta:

**Quais fatores operacionais realmente influenciam a satisfação do cliente e como a empresa pode agir de forma proativa antes da aplicação da pesquisa de NPS?**

## Base de dados

A base utilizada contém dados históricos de pedidos, entregas e interações com o atendimento ao cliente em um contexto de e-commerce.

### Principais grupos de variáveis disponíveis
- Dados do cliente
- Dados do pedido
- Dados logísticos
- Dados de atendimento
- Indicadores internos de negócio
- Nota de NPS

### Variáveis relevantes utilizadas no projeto
- `customer_age`
- `customer_tenure_months`
- `order_value`
- `items_quantity`
- `discount_value`
- `payment_installments`
- `delivery_time_days`
- `delivery_delay_days`
- `freight_value`
- `delivery_attempts`
- `customer_service_contacts`
- `resolution_time_days`
- `complaints_count`
- `nps_score`
- `repeat_purchase_30d`
- `csat_internal_score`

## Metodologia utilizada

A condução do projeto seguiu uma lógica inspirada no CRISP-DM, com foco em entendimento do problema, exploração da base e interpretação orientada a negócio.

### Etapas realizadas
1. **Entendimento do negócio**  
   Definição do problema central e dos possíveis impactos da satisfação do cliente sobre recompra, boca a boca e market share.

2. **Definição da variável alvo**  
   Identificação da variável `nps_score` como medida de satisfação do cliente e criação da variável categórica `nps_category` para a etapa preditiva.

3. **Entendimento e validação da base**  
   Leitura da base, inspeção estrutural, análise de tipos de variáveis, estatísticas descritivas e checagem de valores nulos e duplicados.

4. **Análise Exploratória dos Dados (EDA)**  
   Investigação dos principais fatores associados ao NPS, com foco em:
   - distribuição da satisfação;
   - atraso na entrega;
   - ponto de ruptura por faixas de atraso;
   - reclamações;
   - contatos com atendimento;
   - tempo de resolução;
   - recompra em 30 dias;
   - diferenças por região;
   - correlação entre variáveis numéricas.

5. **Modelagem preditiva**  
   Implementação de um modelo de classificação com `RandomForestClassifier` para prever a categoria de NPS (`Detrator`, `Neutro` ou `Promotor`) com base em sinais operacionais.

6. **Avaliação do modelo**  
   Análise da acurácia, relatório de classificação, matriz de confusão e importância das variáveis, com interpretação prática dos resultados e discussão das limitações.

## Principais insights

De forma geral, os resultados mostraram que a satisfação do cliente está associada principalmente a fatores de atrito na jornada, como:
- atraso na entrega;
- maior volume de reclamações;
- necessidade de múltiplos contatos com o atendimento;
- maior tempo para resolução de problemas.

A análise também indicou que clientes promotores tendem a apresentar jornadas mais fluidas, enquanto detratores concentram mais fricções operacionais. Além disso, a recompra em 30 dias apresentou forte relação com a satisfação, reforçando o impacto do NPS em retenção e continuidade do relacionamento com a marca.

O modelo preditivo apresentou melhor desempenho para identificar clientes detratores, mostrando utilidade prática como ferramenta de alerta para risco de insatisfação.

## Limitações

- A base está desbalanceada, com predominância de clientes detratores.
- O modelo teve dificuldade em distinguir com precisão neutros e promotores.
- Algumas variáveis observadas refletem etapas finais da jornada, o que exige cautela na interpretação preditiva.
- Os resultados devem ser entendidos como apoio à decisão, e não como prova de causalidade.

## Estrutura do repositório

```text
01_analise_nps_fiap.ipynb
desafio_nps_fase_1.csv
README.md
