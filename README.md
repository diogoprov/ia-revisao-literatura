# IA na revisão de literatura

Slides (Quarto + reveal.js) do **workshop de 2 h** *"IA na revisão de literatura: como as ferramentas buscam, onde elas falham e como reportar"*, de Diogo B. Provete (Instituto de Biociências, UFMS · [Biodiversity Synthesis Lab](https://provetelab.org)).

Preparado para o PPG em Biologia Animal. Continuação de [*IA na redação científica*](https://provetelab.org/ia-escrita-cientifica/).

Publicado em **<https://provetelab.org/ia-revisao-literatura/>**.

Público-alvo: pós-graduação em ecologia e zoologia.

## Conteúdo

| Bloco | Tema |
|---|---|
| 0 | De onde viemos: a palestra anterior parou em "declare" |
| 1 | A web que os robôs leem — tráfego automatizado, renderização no cliente, bloqueio de crawlers, e por que **alucinação ≠ bloqueio** |
| 2 | Bases legíveis por máquina: OpenAlex, Semantic Scholar, viés de corpus, API vs. MCP, `openalexR`, `litsearchr` |
| 3 | **Mão na massa**: a mesma pergunta em Consensus e Undermind + OpenAlex em R; sensibilidade vs. precisão; reprodutibilidade |
| 4 | Demonstração: agente com MCP (ferramenta paga — só demo) |
| 5 | Modelos abertos, Co-Scientist, custo/acesso Norte–Sul, e como declarar a busca |

Todas as citações literais foram extraídas dos documentos originais; todos os DOIs e URLs foram verificados.

## Roteiro de tempo (120 min)

São 56 slides, dos quais 6 são aberturas de bloco e 5 são de apoio (referências, links e declaração de IA).

| Bloco | Minutos | Acumulado |
|---|---|---|
| Abertura + como o workshop funciona + bloco 0 | 10 | 0:10 |
| 1 · A web que os robôs leem | 25 | 0:35 |
| 2 · Bases legíveis por máquina | 20 | 0:55 |
| *Intervalo / resolver instalação* | 10 | 1:05 |
| 3 · Mão na massa (inclui 22 min de exercício) | 40 | 1:45 |
| 4 · Demonstração MCP | 10 | 1:55 |
| 5 · Fechamento | 15 | 2:10 |

O bloco 5 estoura em 10 min. **Corte planejado:** se o exercício 1 atrasar (ele vai), os slides que saem sem quebrar o argumento são *"Teoria da internet morta"*, *"Uma lição de medição, de graça"*, *"As outras ferramentas, e onde cada uma entra"* e *"Modelos abertos, rodando na sua máquina"*. Cortando os quatro, volta para 2:00.

Os slides que **não** deveriam sair de jeito nenhum:

- *"O erro de raciocínio que eu quero evitar"* (bloqueio ≠ alucinação) — é a correção conceitual que justifica o workshop inteiro;
- *"A medida que resolve a discussão"* (Lau & Golder 2025) — é a única evidência quantitativa que diz quando usar e quando não usar;
- *"Leia a tabela como estatístico, não como usuário"* — é a transposição do resultado para decisão prática.

## Preparação antes do workshop

**Você (apresentador):**

1. Abrir `radar.cloudflare.com/bots/br` e conferir se o painel carrega — a demonstração 1 depende dele.
2. Testar a demo do bloco 4 com antecedência (a sessão é ao vivo e pode falhar).
3. Levar uma planilha compartilhada (ou o quadro) para coletar os valores de Jaccard da turma.

**Participantes** (mandar por e-mail com 3 dias de antecedência):

- conta gratuita em [Consensus](https://consensus.app) e [Undermind](https://undermind.ai);
- R com `openalexR`, `litsearchr` e `tidyverse`;
- **uma revisão publicada cuja lista de referências conheçam bem** — é o padrão-ouro do exercício.

## Estrutura do repositório

```
index.qmd                     # os slides
custom.scss                   # tema reveal.js com a paleta do site (--bsl-*)
                              #   + classes do workshop (.bsl-exercicio, .bsl-alerta, .cronometro)
_quarto.yml                   # projeto Quarto, output-dir: docs, site-url
assets/qr-provetelab.png      # QR code do slide final
.github/workflows/publish.yml # render + deploy no GitHub Pages
```

## Como renderizar localmente

```bash
quarto render          # gera docs/index.html
quarto preview         # recarrega ao salvar
```

Não há chunks executáveis: o bloco de R nos slides é ilustrativo (`eval: false` por omissão de chunk). O render precisa apenas do Quarto.

`docs/` está no `.gitignore` — a saída é construída pelo GitHub Actions a cada push.

## Licença

Slides, tema e este README sob **[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.pt-br)**.

Atribuição sugerida:

> Provete DB (2026). *IA na revisão de literatura: como as ferramentas buscam, onde elas falham e como reportar.* <https://provetelab.org/ia-revisao-literatura/> — CC BY 4.0

## Declaração de uso de IA

O último slide traz a declaração no formato AIdIT (Drobniak et al. 2026, doi:10.1186/s41073-026-00230-1).
