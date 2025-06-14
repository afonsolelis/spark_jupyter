# 🚀 Aula Prática de Apache Spark com Jupyter

Este repositório contém uma aula completa e prática de Apache Spark usando dados reais de veículos elétricos do estado de Washington (EUA).

## 📋 Conteúdo da Aula

### 🎯 Objetivos
- Comparar processamento **Python puro vs Apache Spark**
- Entender conceitos fundamentais do Spark (RDDs, DataFrames, lazy evaluation)
- Aprender operações essenciais: transformações, ações, window functions
- Praticar **Spark SQL** para consultas complexas
- Implementar **otimizações** (cache, particionamento, broadcast joins)
- Realizar **análise exploratória** de dados reais

### 📊 Dataset
**Arquivo:** `electric_vehicles.json`
- **Fonte:** Washington State Department of Licensing
- **Conteúdo:** Dados de veículos elétricos registrados (BEVs e PHEVs)
- **Campos principais:**
  - Marca, modelo, ano do veículo
  - Tipo (Battery Electric Vehicle ou Plug-in Hybrid)
  - Alcance elétrico, preço MSRP
  - Localização (cidade, condado, coordenadas)
  - Elegibilidade para incentivos

## 🛠️ Configuração do Ambiente

### Pré-requisitos
- Python 3.12+
- Git

### 1. Clone o Repositório
```bash
git clone <url-do-repositorio>
cd spark_jupyter
```

### 2. Instale as Dependências
```bash
pip install -r requirements.txt
```

**Principais bibliotecas instaladas:**
- `pyspark>=3.5.0` - Apache Spark para Python
- `pandas>=2.1.0` - Manipulação de dados
- `numpy>=1.25.0` - Computação numérica
- `matplotlib>=3.8.0` - Visualizações
- `seaborn>=0.13.0` - Visualizações estatísticas
- `jupyterlab>=4.0.0` - Ambiente interativo
- `pyarrow>=14.0.0` - Performance otimizada

### 3. Inicie o Jupyter Lab
```bash
jupyter lab --ip=0.0.0.0 --port=8888 --no-browser --allow-root
```

### 4. Abra o Notebook
Navegue até `spark_aula_veiculos_eletricos.ipynb` e execute as células sequencialmente.

## 📚 Estrutura da Aula

### 1. **Setup e Importações**
- Configuração do ambiente
- Importação das bibliotecas necessárias

### 2. **Carregamento dos Dados**
- Leitura do arquivo JSON
- Estruturação dos dados
- Análise inicial da estrutura

### 3. **Processamento SEM Spark (Python Puro)**
- Implementação de análises usando apenas Python nativo
- Medição de performance
- Análises incluídas:
  - Contagem por marca
  - Distribuição por tipo de veículo
  - Alcance elétrico médio
  - Crescimento temporal
  - Top cidades

### 4. **Setup do Spark**
- Criação da SparkSession
- Configurações otimizadas
- Spark UI para monitoramento

### 5. **Processamento COM Spark**
- Criação de DataFrames
- Implementação das mesmas análises usando Spark
- Comparação de performance

### 6. **Comparação de Performance**
- Análise dos tempos de execução
- Discussão sobre quando usar cada abordagem
- Observações sobre escalabilidade

### 7. **Análise Exploratória dos Dados (EDA)**
- Estatísticas gerais do dataset
- Verificação de dados nulos
- Distribuições por diferentes dimensões

### 8. **Operações Avançadas do Spark**
- **Transformações vs Ações** (lazy evaluation)
- **Window Functions** para análises complexas
- **Spark SQL** para consultas declarativas
- Exemplos práticos de cada conceito

### 9. **Visualizações**
- Gráficos comparativos usando matplotlib/seaborn
- Análise visual dos resultados
- Interpretação dos dados

### 10. **Otimizações e Melhores Práticas**
- Estratégias de particionamento
- Cache e persistência
- Broadcast joins
- Configurações importantes
- Predicate pushdown

### 11. **Análise de Performance e Monitoring**
- Spark UI para debugging
- Planos de execução
- Benchmarks de operações
- Métricas de performance

### 12. **Conclusões e Próximos Passos**
- Resumo dos conceitos aprendidos
- Quando usar Spark vs alternativas
- Caminhos para aprofundamento

## 🔍 Principais Conceitos Demonstrados

### Spark Core
- **RDDs** (Resilient Distributed Datasets)
- **DataFrames** e **Datasets**
- **Transformações** (map, filter, groupBy, join)
- **Ações** (count, collect, show, save)
- **Lazy Evaluation** (otimização automática)

### Spark SQL
- Consultas SQL declarativas
- Registrar DataFrames como tabelas temporárias
- Funções agregadas e window functions
- Subconsultas e CTEs

### Otimizações
- **Cache/Persist** para reutilização de DataFrames
- **Particionamento** por colunas estratégicas
- **Broadcast Joins** para tabelas pequenas
- **Predicate Pushdown** automático
- **Adaptive Query Execution** (AQE)

## 📈 Análises Realizadas

### Análises Básicas
- ✅ Top 10 marcas de veículos elétricos
- ✅ Distribuição BEV vs PHEV
- ✅ Alcance elétrico médio por marca
- ✅ Crescimento de registros por ano
- ✅ Top 10 cidades com mais veículos

### Análises Avançadas
- ✅ Ranking de marcas por ano (Window Functions)
- ✅ Análise geográfica por condado
- ✅ Correlação entre preço e alcance
- ✅ Elegibilidade para incentivos
- ✅ Distribuição de concessionárias elétricas

## 🎯 Casos de Uso do Spark

### ✅ Quando Usar Spark
- Datasets grandes (>1GB)
- Processamento distribuído
- ETL complexo
- Análises em tempo real (Spark Streaming)
- Machine Learning em escala (MLlib)
- Processamento de dados em cluster

### ❌ Quando NÃO Usar Spark
- Datasets pequenos (<100MB)
- Análises simples
- Protótipos rápidos
- Recursos limitados
- Latência ultra-baixa necessária

## 🔧 Troubleshooting

### Problemas Comuns

**Erro de memória:**
```bash
export PYSPARK_DRIVER_PYTHON_OPTS="--max-memory=4g"
```

**Spark UI não carrega:**
- Verifique se a porta 4040 está disponível
- Use `spark.sparkContext.uiWebUrl` para obter a URL

**Performance lenta:**
- Verifique o número de partições com `df.rdd.getNumPartitions()`
- Use cache para DataFrames reutilizados: `df.cache()`
- Considere reparticionamento: `df.repartition(4, "coluna")`

**Erro de Java/Scala:**
- Verifique se JAVA_HOME está configurado
- Spark requer Java 8 ou 11

## 📖 Recursos Adicionais

### Documentação Oficial
- [Apache Spark Documentation](https://spark.apache.org/docs/latest/)
- [PySpark API Reference](https://spark.apache.org/docs/latest/api/python/)

### Próximos Passos
1. **Spark Streaming** - Processamento em tempo real
2. **MLlib** - Machine Learning distribuído
3. **GraphX** - Processamento de grafos
4. **Delta Lake** - Versionamento de dados
5. **Databricks** - Plataforma Spark na nuvem

### Livros Recomendados
- "Learning Spark" - Holden Karau
- "Spark: The Definitive Guide" - Bill Chambers
- "High Performance Spark" - Holden Karau

## 🤝 Contribuição

Sinta-se à vontade para:
- Reportar bugs ou problemas
- Sugerir melhorias
- Adicionar novos exemplos
- Compartilhar casos de uso

## 📄 Licença

Este projeto é para fins educacionais. Os dados utilizados são públicos e fornecidos pelo Washington State Department of Licensing.

---

## 🎉 Divirta-se Aprendendo Spark!

Este tutorial foi criado para proporcionar uma experiência prática e completa com Apache Spark. Execute célula por célula, experimente modificações e explore os dados por conta própria!

**Dica:** Use o Spark UI (normalmente em `http://localhost:4040`) para visualizar os jobs em execução e entender melhor como o Spark processa seus dados.