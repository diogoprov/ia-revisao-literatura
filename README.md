# IA na revisão de literatura

Slides (Quarto + reveal.js) do **workshop de 2 h** *"IA na revisão de literatura: como as ferramentas buscam, onde elas falham e como reportar"*, de Diogo B. Provete (Instituto de Biociências, UFMS · [Biodiversity Synthesis Lab](https://provetelab.org)).

Preparado para o PPG em Biologia Animal. Continuação de [*IA na redação científica*](https://provetelab.org/ia-escrita-cientifica/).

Publicado em **<https://provetelab.org/ia-revisao-literatura/>** · listado em [Teaching → Past courses & short-courses](https://provetelab.org/teaching.html#past-courses-short-courses).

Público-alvo: pós-graduação em ecologia e zoologia.

## Conteúdo

| Bloco | Tema |
|---|---|
| 0 | De onde viemos: a palestra anterior parou em "declare" |
| 1 | **Ver acontecer → entender → medir → contextualizar.** Abre com a demonstração ao vivo de fabricação de referências; depois os dois mecanismos de erro, a escala do problema na literatura publicada, e só então como a web mudou (tráfego automatizado, renderização no cliente, bloqueio de *crawlers*) |
| 2 | Bases legíveis por máquina: OpenAlex, Semantic Scholar, viés de corpus, **o lugar do Google Scholar**, API vs. MCP, `openalexR` e `litsearchr` |
| 3 | **Mão na massa**: a mesma pergunta em Consensus e Undermind + OpenAlex (R ou web); em que estágio o LLM é bom; sensibilidade vs. precisão; reprodutibilidade |
| 4 | Custo e acesso Norte–Sul, e então a demonstração com MCP (ferramenta paga — só demo) |
| 5 | Modelos abertos, Co-Scientist, **a receita em uma página**, e como declarar a busca |

Todas as citações literais foram extraídas dos documentos originais; todos os DOIs foram conferidos no CrossRef ou no PubMed. Dois preprints citados estão marcados como tal nos slides.

## O deck é um superconjunto — escolha a trilha

São **70 slides**. Apresentar tudo leva ~2 h 10. A tabela abaixo é a **trilha de 2 h**; o resto fica no arquivo, que é onde o público relê depois.

| Horário | Bloco | Min |
|---|---|---|
| 0:00 | Abertura, como funciona, bloco 0 | 8 |
| 0:08 | **1 · A web que os robôs leem** (8 min só de demonstração ao vivo) | 30 |
| 0:38 | **2 · Bases legíveis por máquina** | 18 |
| 0:56 | *Intervalo / resolver instalação* | 7 |
| 1:03 | **3 · Mão na massa** (20 + 10 min de exercício) | 40 |
| 1:43 | **4 · Custo, acesso e demonstração MCP** | 10 |
| 1:53 | **5 · Fechamento e a receita** | 12 |

**Reserva (cortar nesta ordem, se atrasar):**

1. *"Teoria da internet morta"* — digressão cultural, não sustenta argumento posterior
2. *"Uma lição de medição, de graça"* (Ülkir & Paslı) — redundante com o slide anterior
3. *"Quem é mais atingido"* — dobra parcialmente com *"E a alucinação não é uniforme no globo"*
4. *"E a qualidade dos metadados"* — vira uma frase; o diagrama de Euler carrega o argumento
5. *"litsearchr"* — vira um link no slide final
6. *"Como fica quando se faz direito"* + *"O detalhe que salta da figura"* — o par custa 4 min
7. *"Modelos abertos, rodando na sua máquina"* — o assunto pede workshop próprio

**Não cortar, em nenhuma hipótese:**

- *"Demonstração ao vivo"* + *"O verificador"* — é o que abre o workshop e o único momento em que eles **veem** acontecer
- *"Por que aquilo aconteceu"* + *"Os dois mecanismos, lado a lado"* — a correção conceitual que justifica o resto
- *"Quanto cada base cobre, em escala"* — o bloco 2 inteiro numa figura
- *"Mas e o Google Scholar?"* + *"A régua aplicada ao Google Scholar"* — é a ferramenta que todos usam; sem isso eles saem sem resposta
- *"A medida que resolve a discussão"* + *"Leia a tabela como estatístico"* + *"A mesma tabela, desenhada"* — a evidência quantitativa que diz quando usar e quando não
- *"A receita, em uma página"* — o slide que vai ser fotografado

## Por que o bloco 1 está nessa ordem

A ordem é deliberada: **experiência → mecanismo → magnitude → contexto**.

A demonstração ao vivo abre o bloco porque prender a sala nos primeiros dez minutos vale mais que qualquer estatística. Só depois vêm os dois mecanismos (que explicam o que acabou de acontecer na tela), depois os números (que dizem o tamanho), e por último como a web mudou — que é a causa do mecanismo B e, sendo contexto, é a parte que se corta primeiro se o relógio apertar.

A versão anterior deste deck fazia o contrário: trinta minutos sobre Cloudflare antes da primeira coisa acontecer.

## Preparação antes do workshop

**Checagens obrigatórias (fazer na véspera):**

1. **Rodar o código do slide "O verificador"** no seu R. Ele usa `httr2`, `purrr` e `tibble` e não foi testado nesta máquina — teste antes, porque ele roda ao vivo na frente da turma.
2. Rodar a **demonstração ao vivo** inteira uma vez, com um tema de teste, e anotar quanto tempo levou de verdade.
3. Abrir `radar.cloudflare.com/bots/br` e conferir se o painel carrega.
4. Testar a demo do bloco 4 (sessão ao vivo com MCP pode falhar).
5. Preparar uma planilha compartilhada (ou o quadro) para os valores de Jaccard da turma.

**Participantes — e-mail com pelo menos uma semana de antecedência.** As contas precisam existir **antes**: criar 25 contas ao vivo trava o exercício, e o plano gratuito do Consensus e do Undermind tem limite de buscas que se gasta rápido se a pessoa ficar testando na hora.

Texto sugerido para o e-mail:

> Para o workshop do dia 19, chegue com três coisas prontas:
>
> 1. **Conta gratuita criada e testada** em consensus.app e undermind.ai — crie agora, faça **uma** busca de teste em cada e não gaste mais que isso; o plano gratuito é limitado e vamos precisar dele no dia.
> 2. **R funcionando** com `openalexR`, `litsearchr`, `httr2` e `tidyverse`. Se não conseguir instalar, tudo bem — há uma alternativa pela web para o exercício.
> 3. **Uma revisão publicada cuja lista de referências você conheça bem** — sua, do seu orientador ou do seu grupo. É o padrão-ouro contra o qual vamos medir o que as ferramentas acham.

## Perguntas que vão aparecer — tenha resposta pronta

A discussão é o objetivo, não o efeito colateral. Estas são as que têm maior chance de vir:

- *"Meu orientador disse para não usar IA nenhuma. E agora?"*
- *"Isso conta como má conduta? Preciso declarar na dissertação, ou só em artigo?"* — puxa para a palestra anterior e para a Portaria CNPq nº 2.664/2026
- *"Qual dessas você usa?"* — desviar soa evasivo; responda com o seu fluxo real
- *"Vale pagar? Qual, se eu só puder pagar uma?"*
- *"E o Google Scholar?"* — agora tem dois slides; se não perguntarem, provoque
- *"E se eu pedir para o ChatGPT com busca ativada? Resolve?"* — é o mecanismo B, não o A
- *"Quanto tempo isso realmente economiza?"* — não há slide com esse número, e é honesto dizer que a evidência mede recall e precisão, não horas

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
