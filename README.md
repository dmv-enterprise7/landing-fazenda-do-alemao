# Landing Fazenda do Alemão — preview de design

Preview da página inicial da **Fazenda do Alemão** (charcutaria artesanal alemã, Mendes/RJ),
produzido pela DMV Enterprise para a Reunião 02 com Otto Grunewald.

> **Isto é um mockup estático.** Não é o site publicado do cliente, não tem back-end
> e não processa pedido nenhum. A página está marcada como preview no topo e no rodapé,
> e sai com `noindex` para não ser indexada.

## O que tem aqui

| Arquivo | O que é |
|---|---|
| `index.html` | A página. Arquivo único, sem build. |
| `DESIGN.md` | A identidade visual do projeto: paleta, tipografia, assinatura, regras de escrita. Leia antes de alterar. |
| `assets/` | Imagens, baixadas do site atual do cliente. Provisórias. |

## Contexto do cliente

Transcrição da reunião, plano de ação e contexto estão no repositório `dmv-gtm-framework`,
em `clientes/_propostas-em-andamento/fazenda-do-alemao/`.

## Antes de alterar qualquer coisa

Leia o `DESIGN.md` e rode o QA visual da skill `dmv-design`:

```bash
node ../dmv-gtm-framework/.claude/skills/dmv-design/scripts/visual-qa.mjs index.html
```

Estado atual: 0 overflow, 0 contraste abaixo de AA, 0 alvo de toque pequeno,
0 controle sem foco ou hover, nos 5 breakpoints.
