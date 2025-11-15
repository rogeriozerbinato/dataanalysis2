# 🏖️ Análise de Airbnb no Rio de Janeiro

## 📋 Sobre o Projeto

Este projeto tem como objetivo **auxiliar turistas na escolha do melhor Airbnb no Rio de Janeiro**, oferecendo insights baseados em dados reais sobre preços, avaliações, localização e tipos de acomodação disponíveis na cidade.

Através de análise exploratória de dados e visualizações intuitivas, este estudo responde perguntas essenciais que todo turista se faz ao planejar sua hospedagem no Rio.

---

## 🎯 Objetivos

- Identificar os bairros com maior oferta de acomodações
- Analisar a distribuição de preços e encontrar o custo médio das diárias
- Avaliar a relação entre tipo de acomodação, preço e avaliações
- Descobrir os Airbnbs melhor avaliados da cidade
- Determinar o melhor custo-benefício por tipo de quarto
- Fornecer insights práticos para tomada de decisão do turista

---

## 📊 Dataset

O dataset contém **3.499 anúncios** de Airbnb no Rio de Janeiro com **78 colunas** de informações, incluindo:

- **Informações do Anúncio**: título, descrição, tipo de propriedade, localização
- **Dados do Anfitrião**: nome, tempo de resposta, taxa de aceitação, verificações
- **Características da Acomodação**: número de quartos, camas, banheiros, comodidades
- **Preços e Disponibilidade**: valor da diária, mínimo/máximo de noites
- **Avaliações**: notas gerais e específicas (limpeza, comunicação, localização, etc.)

### Principais Colunas Analisadas

| Coluna | Descrição |
|--------|-----------|
| `preco` | Valor da diária em dólares |
| `bairro_padronizado` | Nome do bairro |
| `tipo_de_quarto` | Casa/apartamento inteiro, quarto privado, compartilhado |
| `numero_de_avaliacoes` | Quantidade total de avaliações |
| `nota_geral` | Nota de 0 a 500 pontos |
| `acomodacoes` | Número de hóspedes que o local comporta |

---

## 🧹 Processo de Limpeza dos Dados

Para garantir análises precisas e realistas, foram realizadas as seguintes etapas:

### 1. **Formatação de Preços**
```python
# Remoção do símbolo '$' e conversão para float
df_main['preco'] = df_main['preco'].replace('[$,]', '', regex=True).astype(float)
```

### 2. **Tratamento de Outliers**
- Calculado o **Intervalo Interquartil (IQR)** para identificar valores extremos
- Definidos limites baseados em Q1 e Q3
- Removidos preços acima de **$3.050** (mantendo opções de luxo viáveis)
- Resultado: dataset mais representativo da realidade do mercado

**Antes da limpeza**: Preços de $54 a $76.956  
**Após limpeza**: Preços de $54 a $3.050

### 3. **Remoção de Valores Nulos**
- Linhas com preços em branco foram excluídas
- Notas gerais nulas removidas para análises de avaliação

---

## 🔍 Questões Respondidas

### **Questão 1: Quais bairros possuem maior número de acomodações?**

| Bairro | Total de Acomodações |
|--------|---------------------|
| Copacabana | 4.139 |
| Ipanema | 1.420 |
| Barra da Tijuca | 845 |
| Leblon | 695 |
| Botafogo | 589 |

**Insight**: Copacabana lidera disparado, oferecendo quase 3x mais vagas que Ipanema.

---

### **Questão 2: Qual o preço médio das diárias?**

💰 **$526,21** é a média geral após limpeza dos dados.

---

### **Questão 3: Como as avaliações se distribuem por tipo de quarto?**

| Tipo de Quarto | Total de Avaliações |
|----------------|---------------------|
| Casa/apartamento inteiro | 164.978 |
| Quarto privativo | 24.680 |
| Quarto de hotel | 217 |
| Quarto compartilhado | 81 |

**Insight**: Casas/apartamentos inteiros representam **87%** de todas as avaliações.

---

### **Questão 4: Qual a maior e menor nota das avaliações?**

- ⭐ **Maior nota**: 499,0 (escala de 0-500)
- 📉 **Menor nota**: 0,0

---

### **Questão 5: Como são as verificações dos anfitriões?**

O método mais comum é **email + telefone** (2.539 anfitriões), garantindo maior segurança nas reservas.

---

## 💡 Análises Criadas

### **1. Airbnbs Melhor Avaliados do Rio**

| Título | Nota | Avaliações |
|--------|------|-----------|
| Estúdio Copacabana Posto 6 | 499,0 | 222 |
| Fancy suite on the beach | 499,0 | 174 |
| Cobertura com estilo, conforto e privacidade | 499,0 | 173 |

---

### **2. Bairros com Diárias Mais Caras e Mais Baratas**

- 🏆 **Mais caro**: Higienópolis - **$1.500,00** de média
- 💸 **Mais barato**: Quintino Bocaiúva - **$88,00** de média

---

### **3. Melhor Custo-Benefício por Tipo de Quarto**

Calculado através do **índice Nota/Preço** (quanto maior, melhor):

| Tipo de Quarto | Nota Média | Preço Médio | Índice C-B |
|----------------|------------|-------------|-----------|
| Quarto privativo | 302,05 | $330,06 | **0,91** ⭐ |
| Casa/apartamento inteiro | 368,36 | $577,17 | 0,64 |
| Quarto compartilhado | 245,54 | $227,92 | 0,34 |
| Quarto de hotel | 266,50 | $1.290,50 | 0,21 |

**Insight**: Quartos privativos oferecem o melhor equilíbrio entre qualidade e preço!

---

### **4. Bairro Líder em Apartamentos Inteiros**

Copacabana domina com **3.809 vagas** em casas/apartamentos inteiros, sendo a melhor escolha para quem busca privacidade e conforto.

---

## 📈 Visualizações

O projeto inclui **7 gráficos** profissionais:

1. **Boxplots**: Distribuição de variáveis numéricas e preços
2. **Gráfico de Barras**: Top 5 bairros por capacidade
3. **Gráfico de Linha**: Avaliações por tipo de quarto
4. **Gráfico de Barras Horizontal**: Melhores Airbnbs avaliados
5. **Gráfico Comparativo**: Bairros mais caros vs. mais baratos
6. **Gráfico de Índice**: Custo-benefício por tipo de quarto
7. **Gráfico de Pizza**: Distribuição de apartamentos inteiros por bairro

---

## 🛠️ Tecnologias Utilizadas

- **Python 3.x**
- **Pandas**: Manipulação e análise de dados
- **Matplotlib**: Visualizações estáticas
- **Seaborn**: Gráficos estatísticos aprimorados
- **Jupyter Notebook**: Ambiente de desenvolvimento

---

## 🚀 Como Executar

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/analise-airbnb-rio.git

# Instale as dependências
pip install pandas matplotlib seaborn

# Execute o notebook
jupyter notebook analise_airbnb_rio.ipynb
```

---

## 📌 Principais Conclusões para Turistas

✅ **Melhor localização com variedade**: Copacabana  
✅ **Melhor custo-benefício**: Quartos privativos  
✅ **Opção econômica**: Bairros da Zona Norte (ex: Quintino Bocaiúva)  
✅ **Opção premium**: Higienópolis, Ipanema, Leblon  
✅ **Mais avaliado**: Estúdio Copacabana Posto 6 (499 pts, 222 avaliações)  

---

## 📝 Licença

Este projeto é de código aberto e está disponível para uso educacional e analítico.
