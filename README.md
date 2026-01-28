# 1º Hackathon em Controle Social: Desafio Participa DF
## Categoria: Acesso à Informação

### Nome do Projeto
**Classificação Automática de Solicitações com Dados Pessoais (PII)**

### Descrição do Projeto
Este projeto tem como objetivo identificar automaticamente se uma solicitação de acesso à informação contém **dados pessoais sensíveis**, auxiliando órgãos públicos no tratamento adequado das demandas conforme a Lei Geral de Proteção de Dados (LGPD).

A solução utiliza um modelo de **Processamento de Linguagem Natural (PLN)** treinado para classificar textos extraídos de solicitações do Participa DF, indicando se há ou não presença de dados pessoais. O foco é apoiar a transparência pública com responsabilidade e segurança da informação.

---

## Tecnologias Utilizadas
- Python 4.14
- Pandas
- NumPy
- Scikit-learn
- Transformers (Hugging Face)
- PyTorch
- Jupyter Notebook

---

## Autores
- **Autora:** Amanda dos Santos Pereira  
- **Coautora:** Suzany de Almeida Lima  

---

# 1. Instruções de Instalação e Dependências

## 1.1 Pré-requisitos
Antes de iniciar, certifique-se de ter instalado:

- Python **3.9 ou superior**
- Git
- Ambiente Windows (testado em Windows 10+)
- Acesso à internet para download do modelo

> ⚠️ **Observação:** Verifique a **compatibilidade do Python usado**, pois essa versão pode não ser estável em Python recentes que não é suportada pelas bibliotecas utilizadas.

---

## 1.2 Gerenciamento de Pacotes
O projeto utiliza um arquivo `requirements.txt`, que contém todas as dependências necessárias para execução, permitindo a instalação automatizada do ambiente.

Exemplo de dependências incluídas:
```txt
pandas
numpy
torch
transformers
scikit-learn
```

## 1.3 Criação e Configuração do Ambiente

#### 1.3.1 Abra um terminal na pasta raiz do projeto.
Crie um ambiente virtual:
`python -m venv .venv`

#### 1.3.2 Ative o ambiente virtual:
`.venv\Scripts\Activate.ps1`


#### 1.3.3 Instale as dependências:
`pip install -r requirements.txt`

## 2. Criação do Dataset
O dataset foi construído a partir de solicitações reais disponibilizadas pelo `portaldatransparencia.gov.br` em Busca de Pedidos e Respostas dos anos de 2025 e 2024.

Etapas realizadas:
- Limpeza de textos
- Normalização (minúsculas, remoção de caracteres especiais)
- Anonimização
- Rotulagem supervisionada (possui_dados_pessoais = True/False)
- Validação dos rótulos
- Esses processos garantem consistência e confiabilidade para o treinamento do modelo.
- As etapas de criação do dataset estão documentadas no diretório:
`pipelines/dataset_generation`


## 3 Treinamento e Publicação do Modelo

### O treinamento do modelo:

O modelo treinado no notebook `pipelines/training/model_training.ipynb` foi publicado no Hugging Face
🔗 ([https://huggingface.co/amanda2703/pii-distilbert-hackathon](https://huggingface.co/amanda2703/pii-distilbert-hackathon)).


#### Etapas do treinamento:

- Tokenização dos textos

- Fine-tuning do modelo DistilBERT

- Avaliação com métricas de classificação

- Salvamento do modelo final


## 4. Como Rodar o Projeto (Windows)
Requisitos
- Python
- Execução
- Após configurar o ambiente, execute:
- python app/inference.py

> ⚠️ **Observação:** Na primeira execução do script, é esperado um tempo maior de processamento, pois o modelo será baixado e armazenado em cache. Após essa etapa inicial, as execuções subsequentes tendem a ser significativamente mais rápidas.

---
-  Configurações do Script

No arquivo app/inference.py, estão definidas as seguintes variáveis:

```python
MODEL_ID = 'amanda2703/pii-distilbert-hackathon'
FILE_PATH = './app/amostras.csv'
COLUMN_TEXT = 'solicitacao'
COLUMN_LABEL = 'possui_dados_pessoais'
```

Descrição:

* **FILE_PATH**: define o caminho do arquivo CSV que será analisado. O arquivo utilizado é o disponibilizado pelo Hackathon, no qual as classificações foram criadas manualmente.
* **COLUMN_TEXT**: indica a coluna que contém o texto a ser classificado.
* **COLUMN_LABEL**: indica a coluna utilizada para validação das classificações.
Essas três variáveis podem ser ajustadas conforme o arquivo submetido, desde que o formato seja CSV e que a coluna definida em `COLUMN_LABEL` contenha valores booleanos.


> ⚠️ **Regras Extras:** 

O arquivo de entrada deve estar no formato CSV.
A coluna definida em COLUMN_TEXT não pode conter valores nulos.
A coluna COLUMN_LABEL deve conter valores booleanos (True ou False).
Caso a coluna de validação não exista, o script pode ser adaptado para inferência pura (sem validação).
---

## 5. Instruções de Execução
### 5.1 Comando Principal
python app/inference.py

### 5.2 Formato dos Dados

Entrada:
- Arquivo CSV contendo:
- Uma coluna de texto (solicitacao)
- Opcionalmente, uma coluna de rótulo booleano (possui_dados_pessoais)

Saída:
- Classificação automática por linha
- Comparação com rótulos reais (quando disponíveis)
- Métricas de desempenho exibidas no console

## 6. Clareza e Organização
### 6.1 Comentários no Código

O código-fonte contém comentários explicativos em:

- Funções de carregamento do modelo
- Processamento de dados

- Etapas de inferência e validação
Isso facilita a compreensão e manutenção do projeto.

### 6.2 Estrutura de Diretórios
```
.
├── app/ 
│   ├── inference.py 
│   └── amostras.csv 
├── pipelines/ 
│   ├── dataset_generation/ 
│   └── training/ 
├── requirements.txt 
└── README.md 
```

A estrutura separa claramente dados, pipelines, scripts e documentação, seguindo boas práticas de projetos em ciência de dados.
