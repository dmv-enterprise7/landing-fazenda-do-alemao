# DESIGN.md — Fazenda do Alemão

> Identidade visual **deste projeto**. Não é a identidade da DMV nem de outro cliente.
> Criada em 2026-09-11 para o preview de home apresentado na Reunião 02 com Otto Grunewald.
> Entregável: `index.html` — **mockup estático**, sem back-end, sem carrinho.
> Contexto do cliente: `dmv-gtm-framework/clientes/_propostas-em-andamento/fazenda-do-alemao/`

---

## 1. O que esta página é

A home de `fazendadoalemao.com.br` reformulada. Mesma função do site atual — apresentar a marca, os produtos, o restaurante e o como chegar — com a história que o Otto pediu e uma saída clara para a loja online.

**Não é** o site institucional contratado (está fora do escopo do plano v1.0) nem a home do e-commerce. É demonstração, entregue de cortesia, para o Otto reagir antes de qualquer decisão de identidade.

---

## 2. Personalidade

**Enraizado · preciso · caseiro-sem-ser-rústico.**

**Não é:** "artesanal premium" genérico (creme + serifa fina + terracota), não é dark neon, não é sépia de fazendinha.

---

## 3. Por que verde — a decisão competitiva

A concorrência brasileira de charcutaria artesanal (Coldsmoke, Casa Caipira, A Casa do Produtor) roda template de plataforma: fundo branco, grid de 4 colunas, selo de desconto amarelo, nenhuma história. As referências internacionais de herança (Heritage Craft Butchers, Bray Cured) usam dourado sobre branco — luxo genérico.

**Ninguém no setor usa verde.** A Fazenda já é dona do verde pela marca que tem hoje. Manter e aprofundar o verde é o que torna a marca reconhecível numa categoria que é toda vermelha, marrom e creme — e é honesto com a marca existente, o que importa porque o site atual foi feito pela mesma pessoa que fez o site do Restaurante Otto.

---

## 4. Paleta — 5 cores

| Token | Hex | Papel | Origem |
|---|---|---|---|
| `--verde-fazenda` | `#0E2B14` | Fundo escuro dominante | Verde da faixa do logo atual, mais profundo e menos saturado |
| `--verde-mata` | `#16351C` | Superfície elevada sobre o verde | Derivado |
| `--verde-linha` | `#2C5233` | Filetes e divisórias no escuro | Derivado |
| `--dourado` | `#C9A227` | Filetes, rótulos, a assinatura | Dourado da tipografia do logo, dessaturado |
| `--dourado-claro` | `#E7CE7A` | Dourado **legível como texto** sobre verde (6,3:1) | Derivado |
| `--creme` | `#F4EFE2` | Fundo claro | Cor de pão e de toalha |
| `--creme-fundo` | `#EAE2D0` | Superfície recuada no claro | Derivado |
| `--tinta` | `#1A1714` | Texto no claro | — |
| `--tinta-suave` | `#55504A` | Texto secundário (6,9:1) | — |
| `--tijolo` | `#8C3B2A` | **Acento único** — CTA e rótulo de seção | Tijolo da fachada da lojinha |

**Regra dura:** `--dourado` nunca é texto sobre creme (2,1:1). Sobre creme ele é só filete e borda. Como texto, só `--dourado-claro` sobre verde.

O `#ffff00` puro do site atual foi eliminado — é o elemento que mais data a marca.

---

## 5. Tipografia

| Papel | Família | Por que esta |
|---|---|---|
| Display | **Vollkorn** | Antiqua de Friedrich Althausen. "Vollkorn" = grão integral em alemão. Escolha com motivo — não Playfair de reflexo. O itálico carrega o eco da assinatura manuscrita do logo atual. |
| Texto e UI | **Fira Sans** | Erik Spiekermann, Berlim. Grotesca humanista quente. Alemã como o assunto, sem ser caricata. |

Escala em `clamp()`, 7 degraus (`--t-mono` a `--t-ggg`). Nenhum tamanho solto fora dos tokens.

**Calibração de escala (revisada em 2026-09-11):** a primeira versão ficou com sensação de zoom. A escala foi reduzida cerca de 12% em todos os degraus e o container passou de 1180px para **1300px**, que é o que mais tira a sensação de ampliação. O display máximo caiu de 54px para 43px em 1440. A página ficou 11% mais curta (8668px para 7727px) sem perder nenhuma seção.

A foto do hero **não sangra** até a borda da viewport. Sangrava na primeira versão, e isso forçava a imagem original de 703px a esticar 1,5×, produzindo um macro borrado. Contida no grid ela fica em escala ~1:1, nítida, e o enquadramento da travessa inteira aparece. Quando chegarem as fotos originais em alta, o sangramento pode ser reconsiderado.

---

## 6. Sistema de forma

- **Raio:** `2px`, um valor só. Enxaimel é marcenaria, não plástico. Zero elementos com raio ≥ 12px.
- **Sombra:** nenhuma na página inteira. Hierarquia se faz com fundo, filete e espaço.
- **Borda:** filete de 1px; `--verde-linha` no escuro, `rgba(14,43,20,.12–.18)` no claro.
- **Imagem:** corte retangular, sem filtro além de `saturate(1.02) contrast(1.03)`. Nenhuma imagem sangra para fora do container (ver a nota de escala na seção 5).

---

## 6b. A logo e o cabeçalho claro

**O cabeçalho usa a logo original do Otto**, não um wordmark redesenhado. Decisão revista em 2026-09-14.

A primeira versão trocava a faixa por "Fazenda do Alemão" em Vollkorn itálico, com o argumento de que a faixa 3D lustrosa é o elemento mais datado da marca. O argumento estético continua válido, mas perde para o político: rebranding está fora do escopo deste plano, e um preview que remove a marca do cliente desloca a reunião do site para a marca dele, que é onde a conversa trava. O site atual foi feito pela mesma pessoa que fez o do Restaurante Otto.

**Consequência técnica:** a logo é verde sobre transparente. Sobre o verde da página ela vira um borrão e a linha "Receitas originais da Alemanha" some. Ela só funciona em fundo claro. Por isso o cabeçalho é **creme**, e o hero verde começa logo abaixo. Isso não é acidente de layout, é o que o asset exige.

**No rodapé** a marca continua em forma tipográfica, porque o rodapé é verde escuro e não existe variante clara da logo. Quando houver, trocar.

---

## 7. Elemento-assinatura: o enxaimel

A estrutura de madeira do salão do restaurante (foto real do cliente) vira o sistema que organiza a página. Aparece em três formas, e em nenhuma outra:

1. **Cantos de junta** (`.enx`) — L dourado de 34px no canto superior-esquerdo e inferior-direito dos blocos emoldurados.
2. **Travessa** (`.travessa`) — filete horizontal com um losango no centro, como divisor de seção. Usada uma vez, antes do bloco do método.
3. **Treliça** (`.trelica`) — o Andreaskreuz em linhas douradas a 17% de opacidade, preenchendo os três espaços reservados para fotos que ainda não temos.

A treliça é a única razão pela qual a página tem gradiente (3 ocorrências, todas ela). É padrão estrutural, não wash decorativo.

**Por que ela também é honesta:** os três lugares onde a foto não existe ficam marcados como `FOTOGRAFIA A PRODUZIR` em vez de preenchidos com banco de imagem. Isso é argumento de reunião — o Otto vê exatamente onde o material dele falta.

---

## 8. Movimento

Um único momento orquestrado: a revelação escalonada do hero na carga (`sobe`, 0,7s, `cubic-bezier(.22,1,.36,1)`, atrasos de 60–180ms). **Nenhuma** animação de scroll. `prefers-reduced-motion` desliga tudo.

---

## 9. Estrutura da página

Segue a sequência DTC consolidada (hero → prova → benefício → história do fundador → confiança → FAQ → CTA), adaptada ao conteúdo real do site atual:

1. Nav + nota de preview
2. Hero: foto contida, headline, dois CTAs
3. Faixa de credenciais — 1987 · 38 · 23 · Sexta
4. Prova — "se você já comeu Eisbein num restaurante alemão do Rio…"
5. Catálogo por família — nomes reais (Weisswurst, Landrauch, chucrute de vinho…)
6. **O cliente que virou dono** — timeline 1987 / 2004 / 2022 / 2025
7. O método — a citação do toucinho mínimo, do próprio site atual
8. Os lugares — restaurante e lojinha
9. Três formas de comprar + cluster de confiança
10. FAQ de objeções
11. Como chegar + WhatsApp
12. Rodapé + nota de preview

---

## 10. Acessibilidade — verificado, não presumido

Rodadas de `visual-qa.mjs` em 1920/1440/1024/768/390, resultado final:

- **0** overflow horizontal
- **0** contraste abaixo de AA
- **0** alvo de toque < 44px
- **0** controle sem feedback de hover ou foco
- Foco visível com `outline` dourado em todo link, botão e `summary`
- Skip link funcional, escondido com `clip-path`

---

## 11. Regras de escrita

**Nada de travessão (—) no texto visível.** Convenção da casa, a mesma aplicada na apresentação do Botequim Food: travessão em frase curta soa gerado por IA.

- Travessão seguido de complemento curto → **ponto final + frase nova**
- Complemento dependente da frase anterior → **vírgula**
- Em endereço e metadado → **·** (ponto médio)
- Nunca usar travessão no lugar de vírgula ou de dois-pontos

Exceção: apenas separadores decorativos desenhados em CSS.

**Nem o acordeão escapa.** O FAQ usava `+` e `–` como indicador, e o `–` aparecia na tela como traço. Foi trocado por um chevron desenhado com bordas CSS, sem nenhum glifo. Auditoria atual: **zero** travessão ou meia-risca no texto visível, incluindo atributos `alt` e regras `content:`.

---

## 12. Conteúdo: o que é real e o que não é

| Real | Provisório |
|---|---|
| Todos os nomes de produto (do site atual) | Retrato do Otto — placeholder marcado |
| A citação do método (do site atual) | Foto de conservas/pães/doces — placeholder marcado |
| Endereço, WhatsApp, fundação em 1987 | Mapa — placeholder marcado |
| A cronologia 1987/2004/2022/2025 (da transcrição) | Valores de frete mínimo e horário de corte — a definir pelo Otto |
| As 5 fotos (baixadas do site atual) | |

**Nenhum depoimento foi inventado.** A prova social é o fato verificável de que a Fazenda abastece os restaurantes alemães do Rio.

**As fotos estão em baixa resolução** (703px de largura, esticadas). É limitação do material existente — e é exatamente o argumento para o Otto mandar os originais sem tarja verde e sem brasão, como pede o plano de ação.

---

## 13. Para a próxima sessão

- Ao receber as fotos originais: substituir em `assets/` e remover as classes `.trelica` dos três placeholders.
- Não introduzir segunda fonte de verdade de estilo. Os tokens em `:root` mandam.
- Rodar o QA antes de declarar qualquer alteração pronta:
  `node ../dmv-gtm-framework/.claude/skills/dmv-design/scripts/visual-qa.mjs index.html`
