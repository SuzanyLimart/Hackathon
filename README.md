# 1º Hackathon em Controle Social: Desafio Participa DF
## Categoria: Acesso à Informação

### Nome do Projeto
**Classificação Automática de Solicitações com Dados Pessoais (PII)**

### Descrição do Projeto
Este projeto tem como objetivo identificar automaticamente se uma solicitação de acesso à informação contém **dados pessoais sensíveis**, auxiliando órgãos públicos no tratamento adequado das demandas conforme a Lei Geral de Proteção de Dados (LGPD).

A solução utiliza um modelo de **Processamento de Linguagem Natural (PLN)** treinado para classificar textos extraídos de solicitações do Participa DF, indicando se há ou não presença de dados pessoais. O foco é apoiar a transparência pública com responsabilidade e segurança da informação.

---

## Tecnologias Utilizadas
- Python 3.9+
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

> ⚠️ **Observação:** O projeto **não é compatível com Python 4.x**, pois essa versão ainda não é estável e não é suportada pelas bibliotecas utilizadas.

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

####1.3.1 Abra um terminal na pasta raiz do projeto.
1.3.2 Crie um ambiente virtual:
`python -m venv .venv`

####1.3.3 Ative o ambiente virtual:
`.venv\Scripts\Activate.ps1`


####1.3.4. Instale as dependências:
`pip install -r requirements.txt`

## 2. Criação do Dataset
`O dataset foi construído a partir de solicitações reais disponibilizadas pelo Hackathon Participa DF.`

Etapas realizadas:
- Limpeza de textos
- Normalização (minúsculas, remoção de caracteres especiais)
- Anonimização manual
- Rotulagem supervisionada (possui_dados_pessoais = True/False)
- Validação dos rótulos
- Esses processos garantem consistência e confiabilidade para o treinamento do modelo.
- As etapas de criação do dataset estão documentadas no diretório:
`pipelines/dataset_generation`


###2.1 Treinamento e Publicação do Modelo

O treinamento do modelo foi realizado no notebook:
`pipelines/training/model_training.ipynb`

