# Urbanização na planície de inundação do rio Gravataí: análise da enchente de 2024

[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/NicolasTuszynsky/tcc-gravatai-enchente-2024/blob/main/TCC_Nicolas_Analise_Geoespacial_ANOTADO.ipynb)

Material suplementar do Trabalho de Conclusão de Curso em Engenharia Civil — Centro Universitário CESUCA, Cachoeirinha/RS.

**Autor:** Nicolas Mateus Tuszynsky de Moura  
**Orientador:** Prof. Dr. Cristian Jonathan Franco de Lima  
**Coorientador:** Prof. Dr. Laércio Antonio Krein

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
- **Uso e cobertura do solo (2009 e 2024)** — MapBiomas, Coleção 10 (desde nov/2026 o acesso exige um projeto próprio do Earth Engine; ver *Como reproduzir*)
- **Suscetibilidade a inundação** — SGB/CPRM, carta de Gravataí/RS (método HAND)
- **Mancha de inundação de maio de 2024** — Possantti et al. (2024), repositório Zenodo

## Como reproduzir

1. Clique no botão **Abrir no Colab** no topo desta página, ou acesse diretamente:
   <https://colab.research.google.com/github/NicolasTuszynsky/tcc-gravatai-enchente-2024/blob/main/TCC_Nicolas_Analise_Geoespacial_ANOTADO.ipynb>
2. Na **Etapa 0**, substitua o valor de `EE_PROJECT` pelo ID de um projeto **seu** do Google Cloud com o Earth Engine habilitado (ver abaixo por que isso é necessário)
3. Execute **Ambiente de execução → Executar tudo** (no primeiro aviso, confirme "Executar mesmo assim") e autorize o Earth Engine quando solicitado

Todos os dados de entrada são baixados automaticamente — não é preciso ter nenhum arquivo salvo previamente. A conexão com o Google Drive é opcional e serve apenas para guardar uma cópia dos resultados.

### Por que é preciso um projeto do Earth Engine

Os dados de uso e cobertura do solo foram obtidos em **19/08/2026** por acesso direto ao bucket público do MapBiomas em `storage.googleapis.com`, sem nenhum cadastro.

Em **13/11/2026** verificou-se que esse bucket passou a negar `storage.objects.get`, retornando `AccessDenied` tanto para chamadas anônimas quanto para contas Google autenticadas. A Coleção 10 continua pública e gratuita, mas a via de acesso mantida pelo MapBiomas passou a ser o asset no Google Earth Engine.

O notebook tenta primeiro o endereço original — se o acesso público for restabelecido, ele volta a funcionar sem nenhuma alteração — e, se falhar, lê a mesma Coleção 10 pelo asset `projects/mapbiomas-public/assets/brazil/lulc/v1`.

O Earth Engine é gratuito para uso acadêmico e, no nível Comunidade, **não exige conta de faturamento nem cartão de crédito**. O cadastro leva poucos minutos:

1. Acesse <https://code.earthengine.google.com> e registre-se
2. Crie um projeto no Google Cloud e registre-o para **uso não comercial**, nível **Comunidade**
3. Ative a **Google Earth Engine API** no projeto
4. Informe o **ID do projeto** no campo `EE_PROJECT` da Etapa 0

O valor de `EE_PROJECT` que consta no notebook é o projeto do autor e não funciona para outras contas.

As demais bases — IBGE, SGB/CPRM e Possantti et al. (2024) — continuam acessíveis sem qualquer cadastro.

## Ferramentas

Python (`geopandas`, `rasterio`, `shapely`, `geobr`, `matplotlib`, `earthengine-api`, `geemap`), em ambiente Google Colab.
