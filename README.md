# IA na revisão de literatura

Slides (Quarto + reveal.js) do **workshop de 2 h** *"IA na revisão de literatura: como as ferramentas buscam, onde elas falham e como reportar"*, de Diogo B. Provete (Instituto de Biociências, UFMS · [Biodiversity Synthesis Lab](https://provetelab.org)).

Preparado para o PPG em Biologia Animal. Continuação de [*IA na redação científica*](https://provetelab.org/ia-escrita-cientifica/).

Publicado em **<https://provetelab.org/ia-revisao-literatura/>** · listado em [Teaching → Past courses & short-courses](https://provetelab.org/teaching.html#past-courses-short-courses).

Público-alvo: pós-graduação em ecologia e zoologia.

## Conteúdo

| Bloco | Tema |
|---|---|
| 0 | De onde viemos: a palestra anterior parou em "declare" |
| 1 | A web que os robôs leem — tráfego automatizado, renderização no cliente, bloqueio de crawlers, **alucinação ≠ bloqueio**, e a escala do problema medida na literatura publicada |
| 2 | Bases legíveis por máquina: OpenAlex, Semantic Scholar, viés de corpus, API vs. MCP, `openalexR`, `litsearchr` |
| 3 | **Mão na massa**: a mesma pergunta em Consensus e Undermind + OpenAlex em R; em que estágio o LLM é bom; sensibilidade vs. precisão; reprodutibilidade |
| 4 | Demonstração: agente com MCP (ferramenta paga — só demo) |
| 5 | Modelos abertos, Co-Scientist, custo/acesso Norte–Sul, e como declarar a busca |

Todas as citações literais foram extraídas dos documentos originais; todos os DOIs foram conferidos no CrossRef ou no PubMed. Dois preprints citados estão marcados como tal nos slides.

## O deck é um superconjunto — escolha a trilha

São **67 slides**. Apresentar tudo leva ~2 h 20. A tabela abaixo é a **trilha de 2 h**; os slides listados como reserva ficam no arquivo para consulta posterior (o público os lê depois, na web) e para quando o workshop for dado em 3 h.

| Horário | Bloco | Min |
|---|---|---|
| 0:00 | Abertura, como funciona, bloco 0 | 8 |
| 0:08 | **1 · A web que os robôs leem** (inclui a demo ao vivo de 8 min) | 30 |
| 0:38 | **2 · Bases legíveis por máquina** | 15 |
| 0:53 | *Intervalo / resolver instalação* | 7 |
| 1:00 | **3 · Mão na massa** (20 min de exercício) | 40 |
| 1:40 | **4 · Demonstração MCP** | 10 |
| 1:50 | **5 · Fechamento** | 10 |

**Reserva (cortar nesta ordem, se atrasar):**

1. *"Teoria da internet morta"* — é digressão cultural, não sustenta nenhum argumento posterior
2. *"Uma lição de medição, de graça"* (Ülkir & Paslı) — bom, mas redundante com o slide anterior
3. *"Quem é mais atingido"* — dobra parcialmente com *"E a alucinação não é uniforme no globo"*
4. *"E a qualidade dos metadados"* (ORCID, resumos) — vira uma frase; o diagrama de Euler do slide anterior é que carrega o argumento
5. *"litsearchr"* — vira um link no slide final
6. *"Como fica quando se faz direito"* + *"O detalhe que salta da figura"* — o par custa 4 min
7. *"Modelos abertos, rodando na sua máquina"* — o assunto pede um workshop próprio

**Não cortar, em nenhuma hipótese:**

- *"O erro de raciocínio que eu quero evitar"* + *"Os dois mecanismos, lado a lado"* — é a correção conceitual que justifica o workshop
- *"Demonstração ao vivo"* + *"O verificador"* — é o único momento em que eles **veem** acontecer
- *"Em que estágio o LLM é bom — e em qual não é"* + *"O que essa figura resolve para você"* — reorganiza o fluxo de trabalho inteiro
- *"A medida que resolve a discussão"* + *"Leia a tabela como estatístico"* + *"A mesma tabela, desenhada"* — é a evidência quantitativa que diz quando usar e quando não
- *"Quanto cada base cobre, em escala"* — o diagrama de Euler é o argumento inteiro do bloco 2 numa figura

## Preparação antes do workshop

**Checagens obrigatórias (fazer na véspera):**

1. **Rodar o código do slide "O verificador"** no seu R. Ele usa `httr2`, `purrr` e `tibble` e não foi testado nesta máquina — teste antes, porque ele roda ao vivo na frente da turma.
2. Rodar a **demonstração ao vivo** inteira uma vez, com um tema de teste, e anotar quanto tempo levou de verdade.
3. Abrir `radar.cloudflare.com/bots/br` e conferir se o painel carrega.
4. Testar a demo do bloco 4 (sessão ao vivo com MCP pode falhar).
5. Preparar uma planilha compartilhada (ou o quadro) para os valores de Jaccard da turma.

**Participantes** (e-mail com 3 dias de antecedência):

- conta gratuita em [Consensus](https://consensus.app) e [Undermind](https://undermind.ai);
- R com `openalexR`, `litsearchr`, `httr2` e `tidyverse`;
- **uma revisão publicada cuja lista de referências conheçam bem** — é o padrão-ouro do exercício.

## Estrutura do repositório

```
index.qmd                        # os slides
custom.scss                      # tema reveal.js com a paleta do site (--bsl-*)
                                 #   + classes do workshop (.bsl-exercicio, .bsl-alerta, .cronometro)
_quarto.yml                      # projeto Quarto, output-dir: docs, site-url
LICENSE                          # CC BY 4.0 + licenças das figuras de terceiros
assets/qr-provetelab.png         # QR code do slide final
assets/figs/jamia-fig1-workflow.png    # Scherbakov et al. 2025, Fig. 1 (CC BY-NC)
assets/figs/jamia-fig6-desempenho.png  # Scherbakov et al. 2025, Fig. 6 (CC BY-NC)
.github/workflows/publish.yml    # render + deploy no GitHub Pages
```

Os três diagramas esquemáticos (mecanismos de erro; sensibilidade × precisão; cobertura das bases) são **SVG escrito à mão dentro do `index.qmd`**, em blocos ` ```{=html} `. Para editá-los, mexa nas coordenadas ali mesmo — não há arquivo separado.

## Como renderizar e publicar

```bash
quarto render          # gera docs/index.html
quarto preview         # recarrega ao salvar
```

Não há chunks executáveis: o bloco de R nos slides é ilustrativo. O render precisa apenas do Quarto (sem R, sem Python).

`docs/` está no `.gitignore` — a saída é construída pelo GitHub Actions a cada push.

## Depósito no Zenodo (fazer DEPOIS de apresentar)

O `.zenodo.json` na raiz já traz os metadados prontos: título, autoria com ORCID,
afiliação, data, idioma, `upload_type: lesson`, palavras-chave em português e inglês,
identificadores relacionados e a ressalva de licença das figuras.

Passos, na ordem:

1. Apresentar o workshop e incorporar o que a turma mostrar que precisa mudar.
2. Em <https://zenodo.org>, menu do usuário → **GitHub** → ligar o repositório
   `diogoprov/ia-revisao-literatura`.
3. Criar o *release* no GitHub: `gh release create v1.0.0 --title "..." --notes "..."`.
   O Zenodo arquiva e cunha o DOI automaticamente.
4. Conferir o registro. **Um ponto a verificar:** o identificador de licença
   `cc-by-4.0` no `.zenodo.json` não pôde ser validado contra o endpoint
   `/api/licenses` do Zenodo (bloqueado por `robots.txt` — ironia registrada).
   Se o depósito reclamar do campo, escolher *Creative Commons Attribution 4.0
   International* no formulário web; o valor do arquivo é então sobrescrito.
5. Atualizar o `version` do `.zenodo.json` a cada novo release.

O Zenodo cunha **dois** DOIs: um por versão e um *concept DOI* que sempre aponta
para a mais recente. Para citar em Lattes ou relatório, use o concept DOI.

## Licença

Slides, tema, os dois diagramas SVG e este README sob **[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.pt-br)**.

Atribuição sugerida:

> Provete DB (2026). *IA na revisão de literatura: como as ferramentas buscam, onde elas falham e como reportar.* <https://provetelab.org/ia-revisao-literatura/> — CC BY 4.0

As figuras em `assets/figs/` vêm de um artigo de acesso aberto e **mantêm a licença do original** — são **CC BY-NC 4.0**, mais restritiva que a deste repositório. O arquivo [`LICENSE`](LICENSE) detalha a procedência.

## Declaração de uso de IA

O último slide traz a declaração no formato AIdIT (Drobniak et al. 2026, doi:10.1186/s41073-026-00230-1).
