# Análise de Cohort de Retenção de Clientes | Excel + Power Query

Projeto pessoal. Mede **quantos clientes voltam a comprar** nos meses seguintes à primeira compra, agrupando-os pelo mês de aquisição (cohort). Feito só com Excel, Power Query e Tabelas Dinâmicas.

## Pergunta de negócio

> Os clientes voltam a comprar depois da primeira compra? Em quanto tempo? Algum período de aquisição trouxe clientes mais fiéis?

## Dados

- Base pública **Sample Superstore** (varejo fictício dos EUA), 9.994 linhas de itens de pedido, **793 clientes**, pedidos de jan/2014 a dez/2017.
- Abas: `orders`, `customers`, `product`, `location` (originais) → `TABELA TOTAL` (unificada no Power Query) → `cohort` (cálculo e matriz).

## Método

1. Power Query: tipagem das datas e junção de pedidos com clientes e produtos.
2. **Mês de aquisição** = mês da primeira compra do cliente.
3. **Mês decorrido** = diferença em meses entre cada compra e o mês de aquisição.
4. Tabela Dinâmica com **contagem distinta de clientes** por cohort × mês decorrido, mostrada como % do mês 0 (taxa de retenção).
5. Formatação condicional como heatmap.

## Resultados

| Indicador | Valor |
|---|---|
| Retenção média no mês seguinte (M+1) | 6,2% (mediana 2,1%) |
| Retenção média em M+3 | 9,2% |
| Retenção média em M+6 | 8,9% |
| Retenção média em M+12 | 13,6% |
| Clientes que compraram de novo em algum momento | 98% |
| Clientes adquiridos em 2014 | 595 de 793 (75%) |

Leitura:

- A recompra é **pouco frequente mês a mês, mas quase universal no longo prazo**: em um mês específico poucos clientes voltam, porém praticamente todos voltam em algum momento do período.
- A retenção em M+12 é maior que em M+1, sugerindo **ciclo de recompra anual/sazonal** (compras de fim de ano, reposição periódica), e não abandono.
- 75% da base foi adquirida em 2014; os cohorts de 2016–2017 têm poucos clientes (51 e 11), então suas taxas são instáveis e não devem ser comparadas diretamente com as de 2014.

## Recomendações (hipóteses)

- Medir retenção também por **trimestre** para suavizar a sazonalidade.
- Testar campanhas de reativação alinhadas ao ciclo de ~12 meses observado.
- Com mais tempo de dados novos, comparar cohorts recentes com os antigos para avaliar a qualidade da aquisição.

## Limitações

- Base fictícia; sem dados de marketing, então não é possível atribuir causa às variações entre cohorts.
- Cohorts recentes têm menos meses observados (corte em dez/2017).

## Ferramentas

Excel · Power Query · Tabelas Dinâmicas · Formatação condicional
