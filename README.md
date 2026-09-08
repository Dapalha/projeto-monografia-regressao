# Projeto de Monografia — Regressão com Limitador

Este repositório disponibiliza o código-fonte utilizado no projeto de monografia, desenvolvido em Python e executado originalmente no Google Colaboratory (Google Colab).

## 🚀 Executar no Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SEU_USUARIO/SEU_REPOSITORIO/blob/main/Regressao_com_Limitador_GitHub.ipynb)

> **Importante:** substitua `SEU_USUARIO/SEU_REPOSITORIO` pelo endereço real do seu repositório depois de criá-lo.

## 📁 Estrutura esperada da base de dados

A base de dados utilizada pelo notebook é mantida separadamente no Google Drive devido ao seu volume. O notebook espera encontrar:

```text
Meu Drive/
└── dataset_tratado/
    ├── arquivo_01_treated.csv
    ├── arquivo_02_treated.csv
    ├── ...
    ├── arquivo_80_treated.csv
    └── resultados/
```

Os arquivos de entrada devem seguir o padrão:

```text
*_treated.csv
```

### Acesso à base de dados

**Link da pasta compartilhada:** COLE_AQUI_O_LINK_DA_PASTA_DO_GOOGLE_DRIVE

A pasta deve ser compartilhada de acordo com a política de acesso adotada para a banca. Se a pasta for adicionada como atalho ao `Meu Drive` do usuário, o notebook continuará procurando por:

```text
/content/drive/MyDrive/dataset_tratado
```

## 📊 Processamento

O notebook realiza, entre outras etapas:

1. carregamento dos arquivos CSV;
2. engenharia de atributos;
3. cálculo de atributos temporais e espaciais;
4. identificação de eventos;
5. preparação e normalização dos dados;
6. treinamento da regressão logística;
7. avaliação do modelo;
8. geração de métricas e gráficos;
9. análise e ranking de risco por rastreador;
10. salvamento do modelo e demais resultados.

Na execução original, foram carregados 80 arquivos, totalizando aproximadamente 5,7 milhões de registros e 49 atributos após a engenharia de atributos.

## 📦 Resultados

Os resultados são salvos automaticamente em:

```text
dataset_tratado/resultados/
```

Entre os arquivos produzidos pelo notebook estão:

```text
global_metrics.png
sigmoid_function.png
feature_importance.png
ranking_risco_rastreadores.png
relatorio_rastreadores.csv
logistic_model.pkl
scaler.pkl
feature_names.txt
```

## 🛠️ Dependências

As principais bibliotecas utilizadas são:

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Joblib

Instalação:

```bash
pip install -r requirements.txt
```

No Google Colab, as bibliotecas normalmente já estão disponíveis, mas o `requirements.txt` documenta as dependências do projeto.

## ▶️ Passo a passo para a banca

1. Acesse o repositório público no GitHub.
2. Abra `Regressao_com_Limitador_GitHub.ipynb`.
3. Clique em **Open in Colab**.
4. No Colab, autorize o acesso ao Google Drive.
5. Disponibilize a pasta `dataset_tratado` no `Meu Drive`.
6. Confirme que os arquivos `*_treated.csv` estão dentro dessa pasta.
7. Execute as células do notebook em ordem.
8. Os resultados serão criados automaticamente na pasta `resultados`.

## 🔬 Reprodutibilidade

O código foi estruturado para separar:

- **código-fonte:** GitHub;
- **base de dados:** Google Drive;
- **resultados da execução:** pasta `resultados` dentro do diretório da base.

Essa separação evita armazenar a grande base de dados diretamente no repositório e permite que o código permaneça versionado e acessível para consulta e reprodução dos experimentos.

## 🎓 Trabalho acadêmico

Projeto desenvolvido como parte da monografia de conclusão de curso.

**Autor:** SEU NOME  
**Instituição:** SUA INSTITUIÇÃO  
**Curso:** SEU CURSO  
**Ano:** 2026
