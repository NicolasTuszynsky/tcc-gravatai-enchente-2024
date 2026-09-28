# Urbanização na planície de inundação do rio Gravataí: análise da enchente de 2024

Material suplementar do Trabalho de Conclusão de Curso em Engenharia Civil — Centro Universitário CESUCA, Cachoeirinha/RS.

**Autor:** Nicolas Mateus Tuszynsky de Moura  
**Orientador:** Prof. Dr. Laercio Antonio Krein

## Sobre o trabalho

O trabalho analisa as transformações da urbanização sobre a planície de inundação do rio Gravataí, no município de Gravataí/RS, entre 2009 e 2024, tomando a enchente de maio de 2024 como estudo de caso. A análise cruza a mancha urbana, a suscetibilidade a inundação e a extensão real do evento, quantificando as áreas de sobreposição.

## Conteúdo do repositório

| Arquivo | Descrição |
|---|---|
| `TCC_Nicolas_Analise_Geoespacial_ANOTADO.ipynb` | Notebook com todo o processamento geoespacial, comentado etapa por etapa |

O notebook está anotado: antes de cada bloco de código há uma explicação do que foi feito, por que aquela abordagem foi escolhida e quais problemas apareceram no caminho.

## Principais resultados

| Indicador | Valor |
|---|---|
| Área do município | 467,81 km² |
| Área suscetível a inundação | 110,76 km² (23,7% do município) |
| Área urbana 2009 → 2024 | 46,87 → 56,53 km² (+20,6%) |
| Área urbana sobre a planície suscetível | 22,9% → 21,5% |
| Mancha de inundação (maio/2024) | 37,48 km² |
| Área urbana atingida | 2,13 km² (3,8%) |
| Mancha contida na área suscetível | 37,34 km² (99,6%) |
| Expansão urbana recente atingida | 0,50 km² (5,2%) |

Os percentuais de área atingida são estimativas conservadoras: sensores ópticos tendem a subestimar a extensão de água em ambiente urbano denso.

## Fontes de dados

Todas as bases são públicas e gratuitas, e são obtidas automaticamente pelo próprio notebook:

- **Limite municipal** — IBGE, via biblioteca `geobr`
- **Uso e cobertura do solo (2009 e 2024)** — MapBiomas, Coleção 10
- **Suscetibilidade a inundação** — SGB/CPRM, carta de Gravataí/RS (método HAND)
- **Mancha de inundação de maio de 2024** — Possantti et al. (2024), repositório Zenodo

## Como reproduzir

1. Abra o notebook no [Google Colab](https://colab.research.google.com) (Arquivo → Abrir notebook → GitHub, e cole o endereço deste repositório)
2. Execute **Ambiente de execução → Executar tudo**

Não é necessário ter nenhum arquivo salvo previamente: todos os dados de entrada são baixados automaticamente. A conexão com o Google Drive é opcional e serve apenas para guardar uma cópia dos resultados.

## Ferramentas

Python (`geopandas`, `rasterio`, `shapely`, `geobr`, `matplotlib`), em ambiente Google Colab.
