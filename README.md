# Challenge Alura Store

Este projeto faz parte do **Oracle ONE** e é um desafio prático onde a proposta é analisar o desempenho de quatro lojas de e-commerce para decidir qual delas deve ser "vendida". Além disso, há um desafio extra de análise geográfica, que visa melhorar a compreensão do comportamento das lojas em diferentes localizações.

---
## Objetivo

O objetivo principal do projeto é analisar dados de faturamento, vendas, frete, avaliação dos clientes e geolocalização de quatro lojas e, com base em uma série de métricas, decidir qual loja tem o melhor desempenho e qual seria a mais adequada para manter.

---
## Estrutura do Projeto

O projeto está dividido em várias análises, sendo elas:

1. **Análise de Faturamento**: Calcula o faturamento bruto de cada loja com base nas vendas realizadas.
2. **Vendas por Categoria**: Identifica quais categorias de produtos mais se destacam em termos de vendas.
3. **Média de Avaliação das Lojas**: Realiza uma análise da média de avaliação de cada loja com base nas notas fornecidas pelos clientes.
4. **Produtos Mais e Menos Vendidos**: Determina os produtos mais e menos vendidos em cada loja.
5. **Frete Médio por Loja**: Calcula o valor médio do frete de cada loja para determinar quais são as mais econômicas em termos de custos de envio.
6. **Análise de Desempenho Geográfico**: Utiliza gráficos de dispersão para analisar a localização geográfica das lojas e entender se a proximidade de clientes influencia nas vendas.

---
## Metodologia

### 1. **Análise de Faturamento**
Calcula o faturamento bruto de cada loja somando os preços dos produtos vendidos. Esse valor é um dos principais indicadores de performance de vendas.

```python
def faturamento(df) -> float:
    return df['Preço'].sum()
```

### 2. **Vendas por Categoria**
Conta quantas unidades de cada categoria de produto foram vendidas e calcula a porcentagem de vendas por categoria.

```python
def mais_vendidos(df) -> pd.DataFrame:
    contagem = df['Categoria do Produto'].value_counts()
    porcentagem = df['Categoria do Produto'].value_counts(normalize=True) * 100
    return pd.DataFrame({'Quantidade': contagem, 'Porcentagem': porcentagem.round(2)})
```

### 3. **Média de Avaliação das Lojas**
Calcula a média ponderada das avaliações dos clientes, levando em consideração a avaliação de 1 a 5 e seu respectivo peso.

```python
def avaliacao_da_loja(df) -> float:
    contador = df['Avaliação da compra'].value_counts().sort_index()
    avaliacoes = contador.index
    valores = contador.values
    return round(sum(avaliacoes * valores) / len(df['Avaliação da compra']), 2)
```

### 4. **Produtos Mais e Menos Vendidos**
Identifica o produtos mais vendidos e o menos vendidos de cada loja, ajudando a entender os comportamentos de compra dos cliente

```python
def produtos_vendidos(df) -> list:
    produtos = df['Produto'].value_counts()
    mais_vendidos = produtos.head(1).index[0]
    quantidade_mais_vendida = produtos.head(1).values[0]
    menos_vendidos = produtos.tail(1).index[0]
    quantidade_menos_vendida = produtos.tail(1).values[0]
    return [mais_vendidos, quantidade_mais vendida, menos_vendidos, quantidade_menos_vendida]
```

### 5. **Frete Médio por Loja**
Calcula o custo médio de frete por loja e compara as diferentes opções para ver qual oferece o melhor custo-benefício.

```python
def media_do_frete(df) -> float:
    return round(df['Frete'].sum() / len(df['Frete']), 2)
```
### 6. **Análise de Desempenho Geográfico**
Usando gráficos de dispersão, é possível visualizar a localização geográfica das lojas e sua relação com o desempenho de vendas.

```python
plt.scatter(loja['lon'], loja['lat'], alpha=0.3, label='Loja_1', color='#0000FF')
```
---
## Como rodar o projeto

Para rodar este Projeto em sua máquina, siga os seguintes passos :

### 1. **Clone o repositório**

```bash
git clone https://github.com/usuario/Challenge-Alura-Store.git corrigir
```
### 2. **Instale as dependências**

```bash
pip install -r requirements.txt
```

### 3. **Execute o código**

```bash
python main.py
```
---
## Licença

Este projeto ésta sob a **Licença MIT**.
