#treemap

Nucleos e maquinas virtuais não possuem monitoramento de temperatura pela ausencia de drive fisico do tipo IC2.

Isso leva a necessidade de predicação reativa (temperatura de nucleos fisicos e virtuais) consumo de cpu memoria usuarios e rede (preditivo)

Para adicionar o treemap com informações de temperatura, consumo de CPU, memória e energia para os núcleos de CPU, TPU, GPU e QPU do Google, e atualizar o projeto com versão e data, podemos seguir as etapas a seguir.

Atualização da Estrutura do Repositório:

A nova estrutura do repositório será ajustada para incluir a parte de monitoramento de recursos e visualização. Abaixo estão as atualizações:

    quantum-climate-prediction-system/
    │
    ├── src/
    │   ├── quantum_simulator/
    │   ├── classical_simulator/
    │   ├── data/
    │   ├── models/
    │   ├── utils/
    │   ├── monitoring/               # Nova pasta para monitoramento de recursos
    │   │   ├── resource_monitor.py    # Monitoramento de CPU, GPU, TPU, QPU, etc.
    │   │   ├── treemap_visualization.py # Função para gerar o treemap
    │
    ├── tests/
    │   ├── test_quantum_simulator.py
    │   ├── test_classical_simulator.py
    │   └── test_prediction_models.py
    │
    ├── notebooks/
    │   ├── temperature_analysis.ipynb
    │   └── quantum_model_experiments.ipynb
    │
    ├── requirements.txt
    ├── Dockerfile
    ├── README.md
    └── .gitignore

Detalhamento dos Arquivos Adicionados/Atualizados:

1. resource_monitor.py (Novo arquivo em src/monitoring/): Esse script será responsável por coletar informações de temperatura, consumo de CPU, memória e energia de cada núcleo da CPU, TPU, GPU e QPU, utilizando bibliotecas como psutil, gpustat e outras para capturar os dados de recursos de hardware.
    
    
    
    import psutil
    import gpustat
    import datetime
    
    def get_system_resources():
        # Captura a utilização de CPU, memória e temperatura
        cpu_usage = psutil.cpu_percent(interval=1)
        memory_info = psutil.virtual_memory()
        memory_usage = memory_info.percent
        cpu_temperature = psutil.sensors_temperatures().get('coretemp', [])
    
        # Captura a utilização de GPU usando gpustat
        gpu_stats = gpustat.new_query()
    
        # Formatação dos dados
        resources = {
            'cpu_usage': cpu_usage,
            'memory_usage': memory_usage,
            'cpu_temperature': cpu_temperature[0].current if cpu_temperature else None,
            'gpu_usage': gpu_stats.gpus[0].memory_used,  # Exemplo de GPU, pode ser ajustado para múltiplas GPUs
            'gpu_memory_total': gpu_stats.gpus[0].memory_total,
            'timestamp': datetime.datetime.now().isoformat()
        }
    
        return resources

2. treemap_visualization.py (Novo arquivo em src/monitoring/): Este script usará uma biblioteca como plotly para criar um treemap visual com as informações de temperatura, consumo de CPU, memória e energia.



import plotly.express as px
import pandas as pd

def generate_treemap(data):
    # Suponhamos que 'data' seja um dicionário com os recursos coletados
    df = pd.DataFrame(data)
    
    # Exemplo de criação do treemap
    fig = px.treemap(df, 
                     path=['cpu_usage', 'memory_usage', 'gpu_usage'], 
                     values='cpu_temperature', 
                     title='Monitoramento de Temperatura e Consumo de Recursos')
    
    fig.show()

Atualizações no README.md:

No arquivo README.md, serão feitas as atualizações de versão e a descrição das novas funcionalidades de monitoramento e visualização.

# Quantum Climate Prediction System (QCPS)

Este projeto utiliza simuladores clássicos e quânticos para prever as temperaturas futuras de Londres, a partir de dados históricos de 1940 a 2020. A previsão também inclui a temperatura nos núcleos dos data centers do Google em Londres. O objetivo é melhorar as previsões climáticas e otimizar os sistemas de resfriamento de data centers.

## Tecnologias Utilizadas
- Python 3.8+
- Quantum Computing (simulação quântica)
- Machine Learning
- Docker
- Monitoramento de Recursos (CPU, GPU, TPU, QPU)

## Estrutura do Repositório
- `src/`: Contém o código-fonte principal do projeto.
- `tests/`: Contém testes automatizados.
- `notebooks/`: Notebooks para análise e experimentação.
- `requirements.txt`: Arquivo de dependências.
- `Dockerfile`: Para criação de containers Docker.
- `README.md`: Este documento.
- `src/monitoring/`: Funções para monitoramento de recursos e visualização de treemaps.

## Como Rodar
1. Clone este repositório:
    ```bash
    git clone https://github.com/username/quantum-climate-prediction-system.git
    cd quantum-climate-prediction-system
    ```
2. Instale as dependências:
    ```bash
    pip install -r requirements.txt
    ```

3. Execute os testes:
    ```bash
    pytest tests/
    ```

4. Rodando o simulador:
    ```bash
    python src/quantum_simulator/simulator.py
    ```

5. Para monitorar os recursos:
    ```bash
    python src/monitoring/resource_monitor.py
    ```

## Contribuições

Sinta-se à vontade para enviar problemas e pull requests para contribuir com o projeto.

## Autor
José Soares Sobrinho

## Licença
Este projeto está licenciado sob a MIT License.

Atualização do Dockerfile:

O Dockerfile também precisará de atualizações para garantir que as novas dependências, como psutil, gpustat e plotly, sejam instaladas corretamente.

# Base image
FROM python:3.8-slim

# Set working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libatlas-base-dev \
    libssl-dev \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the project files
COPY . .

# Set the command to run the app
CMD ["python", "src/quantum_simulator/simulator.py"]

Atualizações de Versão e Data:

O arquivo README.md e os scripts Python podem ser atualizados com tags de versão e data, como exemplificado no código-fonte de resource_monitor.py:

__version__ = "1.0.1"
__date__ = "2025-03-17"

Essas mudanças ajudam a manter o controle da versão do projeto e das atualizações que foram feitas.

