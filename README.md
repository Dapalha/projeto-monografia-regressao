# Projeto de Monografia — Regressão com Limitador

Repositório destinado à disponibilização do código-fonte utilizado no projeto de monografia.

O código foi desenvolvido em Python e estruturado para execução no Google Colaboratory (Google Colab), utilizando uma base de dados armazenada separadamente no Google Drive.

## Abrir no Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Dapalha/projeto-monografia-regressao/blob/main/Regressao_com_Limitador.ipynb)

## Estrutura do repositório

```text
projeto-monografia-regressao/
├── README.md
├── Regressao_com_Limitador.ipynb
├── requirements.txt
└── .gitignore
```

## Base de dados

A base de dados utilizada pelo projeto é mantida separadamente no Google Drive devido ao seu volume.

Estrutura esperada:

```text
Meu Drive/
└── dataset_tratado/
    ├── arquivo_01_treated.csv
    ├── arquivo_02_treated.csv
    ├── ...
    ├── arquivo_80_treated.csv
    └── resultados/
```

Os arquivos de entrada devem possuir o padrão:

```text
*_treated.csv
```

### Link da base de dados

**https://drive.google.com/drive/folders/1vWRL0WtCI7Sl2JTjXNsoze-_mW5xlLAp?usp=drive_link**

> A base deve ser disponibilizada de acordo com as regras de acesso e confidencialidade aplicáveis ao trabalho acadêmico.

## Como executar

1. Acesse este repositório.
2. Abra `Regressao_com_Limitador.ipynb`.
3. Clique em **Open in Colab**.
4. Autorize o acesso ao Google Drive.
5. Disponibilize a pasta `dataset_tratado` em `Meu Drive`.
6. Confirme que os arquivos `*_treated.csv` estão dentro da pasta.
7. Execute as células do notebook em ordem.
8. Os resultados serão gravados automaticamente em `dataset_tratado/resultados/`.

O notebook verifica automaticamente se a pasta da base existe e se foram encontrados arquivos de entrada.

## Processamento

O notebook realiza as etapas computacionais definidas no projeto, incluindo carregamento dos arquivos, engenharia de atributos, preparação dos dados, treinamento e avaliação do modelo, análise individual por rastreador, geração de gráficos e salvamento do modelo treinado.

## Resultados

Os resultados são gerados na pasta:

```text
dataset_tratado/resultados/
```

Entre os arquivos gerados pelo notebook estão:

```text
classification_report_train.png
classification_report_val.png
individual_tracker_report.png
ranking_risco_rastreadores.png
relatorio_rastreadores.csv
logistic_model.pkl
scaler.pkl
feature_names.txt
```

## Dependências

As principais bibliotecas utilizadas são:

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Joblib

As dependências estão documentadas em `requirements.txt`.

## Reprodutibilidade

A organização do projeto separa os três elementos principais:

- **Código:** GitHub;
- **Base de dados:** Google Drive;
- **Resultados da execução:** pasta `resultados` no Google Drive.

## Informações acadêmicas

**Autor:** Gustavo Luiz Ribeiro da Cruz  
**Instituição:** CEFET/RJ  
**Curso:** Bacharelado em Engenharia Eletrônica  
**Ano:** 2026
