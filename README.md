# Detecção de fraudes em rastreadores veiculares

Código do Trabalho de Conclusão de Curso *Desenvolvimento e simulação de um sistema de detecção de fraudes em rastreadores veiculares*, Engenharia Eletrônica, CEFET/RJ.

O sistema recebe a planilha de auditoria de um rastreador e indica se houve fraude, comparando três classificadores: **Regressão Logística**, **Rede Neural (MLP)** e **XGBoost**.

## Notebooks

Os notebooks são autossuficientes: o código reutilizável (pacote `fraude/`) está embutido em células `%%writefile` no início de cada um, e as dependências são instaladas pela primeira célula. Não é preciso clonar o repositório para executá-los.

| Notebook | Conteúdo | Colab |
|---|---|---|
| [01_treinamento_e_avaliacao](notebooks/01_treinamento_e_avaliacao.ipynb) | tratamento dos dados, montagem da base, experimentos, figuras e modelos finais | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Dapalha/projeto-monografia-regressao/blob/main/notebooks/01_treinamento_e_avaliacao.ipynb) |
| [02_classificador](notebooks/02_classificador.ipynb) | classificação de um arquivo, ranking de uma pasta e interface web | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Dapalha/projeto-monografia-regressao/blob/main/notebooks/02_classificador.ipynb) |

## Estrutura

```
projeto-monografia-regressao/
├── notebooks/
│   ├── 01_treinamento_e_avaliacao.ipynb
│   └── 02_classificador.ipynb
├── requirements.txt         versões mínimas das bibliotecas (uso fora do Colab)
└── README.md
```

O pacote `fraude/` é gravado na pasta de trabalho quando o notebook é executado. Os módulos são:

| Módulo | Função | Notebook |
|---|---|---|
| `tratamento.py` | leitura e limpeza das planilhas de auditoria | 01 e 02 |
| `features.py` | variáveis por registro, janelas e decisão combinada | 01 e 02 |
| `figuras.py` | figuras da monografia | 01 e 02 |
| `base.py` | montagem da base e rótulos confirmados | 01 |
| `modelos.py` | Regressão Logística, MLP e XGBoost | 01 |
| `avaliacao.py` | métricas por janela e por rastreador | 01 |
| `analise.py` | classificação de um arquivo | 02 |
| `interface.py` | interface web (Gradio) | 02 |

## Dados

A base não fica no repositório por causa do volume e da confidencialidade. Estrutura esperada no Google Drive:

```
Meu Drive/
├── dados_brutos/            planilhas *_auditoria.csv ou .xlsx
└── dataset_tratado/         *_treated.csv (gerados pelo notebook 01)
    └── resultados/
        ├── fraudes_confirmadas.csv   opcional: rastreador;inicio;fim
        ├── modelos_finais.pkl
        └── figuras/
```

Link da base: https://drive.google.com/drive/folders/1vWRL0WtCI7Sl2JTjXNsoze-_mW5xlLAp?usp=drive_link

## Metodologia

- **Tratamento:** datas e durações viram tipos temporais antes do one-hot-encoding; coordenadas, acentuação e linhas com ';' extra são corrigidas.
- **Unidade de análise:** janelas de 60 minutos de um único rastreador, com variáveis calculadas em relação ao próprio rastreador.
- **Rótulo:** jammer com duração de pelo menos 30 minutos e/ou violação de alimentação (energia externa cortada com o veículo em movimento e ignição desligada). Períodos confirmados, quando disponíveis, substituem a regra.
- **Reason Codes:** códigos de diferentes fabricantes (CalAmp, Concox, MXT, Newtec, Sertec, Suntech, Queclink) agrupados em famílias de evento.
- **Avaliação sem vazamento:** imputação e padronização dentro de um Pipeline ajustado só no treino; protocolo temporal e protocolo por grupos (StratifiedGroupKFold).
- **Limiar:** escolhido na validação para atingir precisão mínima de 50%.
- **Decisão:** um arquivo só é classificado como fraude se algum episódio reunir pelo menos dois tipos de indício e o risco combinado atingir 50%.

## Execução

1. Abra o notebook 01 no Colab (botão acima) e autorize o acesso ao Google Drive.
2. Execute as células de preparação do ambiente e as da seção "Código do pacote fraude", na ordem.
3. Na primeira execução, use `TRATAR_DADOS_BRUTOS = True` e `RECONSTRUIR_BASE = True`.
4. Execute as demais células. As figuras ficam em `resultados/figuras` e os modelos em `resultados/modelos_finais.pkl`.
5. Abra o notebook 02 para classificar arquivos, gerar o ranking de uma pasta ou abrir a interface web (`launch(share=True)` gera um link público válido por 72 horas).

Fora do Colab, instale as dependências com `pip install -r requirements.txt` e ajuste a variável `DRIVE` na célula de configuração para a pasta local com os dados.

O modelo salvo deve ser aberto com as mesmas versões de bibliotecas usadas no treinamento.
