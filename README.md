# Uso do Azure Speech Studio e do Azure Language Studio

## Introdução

Este guia descreve como utilizar o **Azure Speech Studio** para tarefas relacionadas à fala e o **Azure Language Studio** para análise linguística, incluindo mineração de sentimentos e opiniões.

## Pré-requisitos

Antes de começar, verifique se você possui:
- Uma conta ativa no Azure.
- Acesso aos recursos do Azure Speech Studio e Language Studio.
- Conhecimentos básicos de serviços do Azure.

---

## Passo a Passo

### 1. Acessando o Azure Speech Studio
1. Vá até o portal do Azure ([portal.azure.com](https://portal.azure.com)) e faça login.
2. Pesquise por "Speech Studio" e selecione o serviço nos resultados.
3. Explore recursos como **Conversão de Fala em Texto**, **Texto em Fala** e **Tradução de Fala**.

![print1](https://github.com/ItaloRochaj/language-studio/blob/main/assets/print1.png)

#### Criando um Recurso de Fala
1. No Speech Studio, clique em **"Criar um recurso"**.
2. Preencha os detalhes necessários, como assinatura, grupo de recursos e região.
3. Escolha o plano de preços apropriado.
4. Clique em **"Revisar + criar"** e depois em **"Criar"**.

![print2](assets/criar_recurso.png)

---

### 2. Acessando o Azure Language Studio
1. No portal do Azure, pesquise por "Language Studio".
2. Selecione o serviço **Language Studio**.
3. Explore funcionalidades como análise de sentimentos, extração de frases-chave e detecção de idioma.

![print3](assets/language_studio.png)

---

### 3. Mineração de Sentimentos e Opiniões no Language Studio

#### Configurando a Análise
1. Acesse o recurso **"Sentiment and opinion mining tryout"**.
2. Escolha o idioma do texto no menu suspenso (ex.: inglês ou português).
3. Conecte-se a um recurso Azure (plano gratuito F0 recomendado).
4. Insira o texto a ser analisado na caixa de texto. Você também pode usar arquivos ou textos de exemplo.

![print4](assets/configurar_analise.png)

#### Habilitando a Mineração de Opiniões
1. Ative a opção **"Opinion mining"** para obter análises detalhadas sobre palavras ou atributos específicos.
2. Clique em **"Analyze"** para processar o texto.

![print5](assets/habilitar_mineracao.png)

#### Interpretando os Resultados
- Sentimentos são classificados como **negativo**, **neutro** ou **positivo**.
- As pontuações de confiança aparecem em níveis de sentença e documento.
- Caso a mineração de opinião esteja ativada, veja insights detalhados sobre palavras e atributos analisados.

![print6](assets/resultados.png)

---

## Exemplo de Saída de Análise

Aqui está um exemplo de saída JSON gerada pela análise de sentimentos:

```json
{
    "documents": [
        {
            "id": "id__1177",
            "sentiment": "negative",
            "confidenceScores": {
                "positive": 0,
                "neutral": 0,
                "negative": 1
            },
            "sentences": [
                {
                    "sentiment": "negative",
                    "confidenceScores": {
                        "positive": 0,
                        "neutral": 0,
                        "negative": 1
                    },
                    "offset": 0,
                    "length": 220,
                    "text": "Tired hotel with poor service   The Royal Hotel, London, UK   06/05/2018   This is an old hotel (dating back to the 1950s), and the room furniture is average – already getting a bit worn out and in need of replacement. ",
                    "targets": [
                        {
                            "sentiment": "negative",
                            "confidenceScores": {
                                "positive": 0.02,
                                "negative": 0.98
                            },
                            "offset": 7,
                            "length": 5,
                            "text": "hotel",
                            "relations": [
                                {
                                    "relationType": "assessment",
                                    "ref": "#/documents/0/sentences/0/assessments/0"
                                }
                            ]
                        },
                        {
                            "sentiment": "negative",
                            "confidenceScores": {
                                "positive": 0.01,
                                "negative": 0.99
                            },
                            "offset": 23,
                            "length": 7,
                            "text": "service",
                            "relations": [
                                {
                                    "relationType": "assessment",
                                    "ref": "#/documents/0/sentences/0/assessments/1"
                                }
                            ]
                        }
                    ],
                    "assessments": [
                        {
                            "sentiment": "negative",
                            "confidenceScores": {
                                "positive": 0.02,
                                "negative": 0.98
                            },
                            "offset": 0,
                            "length": 6,
                            "text": "Tired",
                            "isNegated": false
                        },
                        {
                            "sentiment": "negative",
                            "confidenceScores": {
                                "positive": 0.01,
                                "negative": 0.99
                            },
                            "offset": 18,
                            "length": 4,
                            "text": "poor",
                            "isNegated": false
                        }
                    ]
                }
            ],
            "warnings": []
        }
    ],
    "errors": [],
    "modelVersion": "2025-01-01"
}