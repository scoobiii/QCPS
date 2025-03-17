#datasets

Para obter os dados de temperatura de Londres entre 1940 e 2020, você pode utilizar fontes públicas de dados climáticos. Abaixo estão algumas opções confiáveis para obter esses dados:

---

### 1. **Met Office (UK Meteorological Office)**
   - **Descrição**: O Met Office é a agência nacional de meteorologia do Reino Unido e fornece dados históricos de temperatura para Londres e outras regiões.
   - **Link**: [Met Office Data](https://www.metoffice.gov.uk/)
   - **Como acessar**:
     1. Visite o site do Met Office.
     2. Navegue até a seção de dados climáticos históricos.
     3. Selecione a localização (Londres) e o período desejado (1940–2020).
     4. Baixe os dados em formato CSV ou similar.

---

### 2. **NOAA (National Oceanic and Atmospheric Administration)**
   - **Descrição**: A NOAA fornece dados climáticos globais, incluindo temperaturas históricas para várias cidades, incluindo Londres.
   - **Link**: [NOAA Climate Data Online](https://www.ncei.noaa.gov/cdo-web/)
   - **Como acessar**:
     1. Acesse o portal de dados climáticos da NOAA.
     2. Use a ferramenta de busca para selecionar a localização (Londres) e o período (1940–2020).
     3. Escolha os parâmetros de temperatura (média, máxima, mínima).
     4. Baixe os dados em formato CSV.

---

### 3. **World Weather Online**
   - **Descrição**: World Weather Online oferece dados históricos de temperatura para várias cidades, incluindo Londres.
   - **Link**: [World Weather Online Historical Data](https://www.worldweatheronline.com/)
   - **Como acessar**:
     1. Visite o site e selecione a opção de dados históricos.
     2. Insira a localização (Londres) e o período desejado (1940–2020).
     3. Baixe os dados em formato CSV.

---

### 4. **Climate Data Online (CDO)**
   - **Descrição**: O Climate Data Online é uma plataforma que reúne dados climáticos de várias fontes, incluindo estações meteorológicas em Londres.
   - **Link**: [Climate Data Online](https://www.climate.gov/maps-data/dataset)
   - **Como acessar**:
     1. Navegue até a seção de dados históricos.
     2. Selecione a localização (Londres) e o período (1940–2020).
     3. Baixe os dados em formato CSV.

---

### 5. **Kaggle**
   - **Descrição**: Kaggle é uma plataforma de ciência de dados que oferece conjuntos de dados públicos, incluindo dados climáticos.
   - **Link**: [Kaggle Datasets](https://www.kaggle.com/datasets)
   - **Como acessar**:
     1. Pesquise por "London temperature data" ou "UK historical weather data".
     2. Verifique se há conjuntos de dados que cobrem o período de 1940 a 2020.
     3. Baixe o dataset diretamente da plataforma.

---

### 6. **OpenWeatherMap**
   - **Descrição**: OpenWeatherMap fornece dados climáticos históricos e em tempo real para várias cidades, incluindo Londres.
   - **Link**: [OpenWeatherMap Historical Data](https://openweathermap.org/history)
   - **Como acessar**:
     1. Crie uma conta gratuita ou paga (dependendo do volume de dados necessários).
     2. Use a API ou a interface web para buscar dados históricos de Londres.
     3. Baixe os dados em formato JSON ou CSV.

---

### 7. **European Climate Assessment & Dataset (ECA&D)**
   - **Descrição**: A ECA&D fornece dados climáticos históricos para a Europa, incluindo o Reino Unido.
   - **Link**: [ECA&D Data](https://www.ecad.eu/)
   - **Como acessar**:
     1. Navegue até a seção de dados.
     2. Selecione a localização (Londres) e o período (1940–2020).
     3. Baixe os dados em formato CSV.

---

### 8. **Google Dataset Search**
   - **Descrição**: Ferramenta do Google para buscar conjuntos de dados públicos.
   - **Link**: [Google Dataset Search](https://datasetsearch.research.google.com/)
   - **Como acessar**:
     1. Pesquise por "London temperature data 1940–2020".
     2. Verifique os resultados e baixe os datasets disponíveis.

---

### Estrutura do Dataset Esperado:
O dataset de temperatura de Londres deve conter colunas como:
- **Data**: Data da medição (formato YYYY-MM-DD).
- **Temperatura Média**: Temperatura média do dia.
- **Temperatura Máxima**: Temperatura máxima do dia.
- **Temperatura Mínima**: Temperatura mínima do dia.
- **Precipitação**: Dados de chuva (opcional).
- **Outros Parâmetros**: Umidade, velocidade do vento, etc. (opcional).

---

### Passos para Inserir os Dados no Projeto:
1. Baixe o dataset de uma das fontes acima.
2. Coloque o arquivo na pasta `data/raw/` com o nome `london_temperature_1940_2020.csv`.
3. Use o script `data_cleaning.py` na pasta `src/data_processing/` para limpar e preparar os dados.
4. Salve os dados processados na pasta `data/processed/` como `cleaned_london_temperature.csv`.

---

### Exemplo de Código para Carregar os Dados:
```python
import pandas as pd

# Carregar dados brutos
raw_data_path = "data/raw/london_temperature_1940_2020.csv"
raw_data = pd.read_csv(raw_data_path)

# Exibir as primeiras linhas
print(raw_data.head())
```

---

Com esses dados, você poderá prosseguir com a análise, modelagem clássica e simulações quânticas para prever a temperatura em Londres. Se precisar de ajuda adicional para processar ou analisar os dados, é só avisar!
