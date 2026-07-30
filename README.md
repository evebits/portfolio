# Handoff: Portfólio Evelyn Bitencourt (staff service designer)

## Overview
Portfólio pessoal multi-página: hub (`Portfolio.dc.html` → deve virar `index.html` no deploy) com hero, "Sobre mim" e carrossel de projetos, mais 7 páginas de estudo de caso individuais.

## About the Design Files
Os arquivos deste pacote são **referências de design construídas em HTML** — protótipos de alta fidelidade mostrando aparência e comportamento pretendidos, não código de produção para copiar diretamente. A tarefa é **recriar este design HTML no ambiente de destino** (site estático, Next.js, etc.) escolhido pelo desenvolvedor, usando os padrões já estabelecidos nesse ambiente, ou HTML/CSS estático simples caso não haja necessidade de framework.

## Fidelity
**Alta fidelidade (hifi)**: cores, tipografia, espaçamento e conteúdo finais. Recrie pixel a pixel.

## Screens / Views
1. **Hub (`Portfolio.dc.html`)** — Header fixo (nav: Página Principal / Sobre mim / Projetos / Contato), Hero (nome + slogan + retrato, grid 12 colunas), Sobre mim (bio + retrato), Projetos (carrossel horizontal com scroll-snap, 7 cards, setas ← →), Contato (rodapé com CTA + e-mail/telefone/site).
2. **Páginas de projeto** (`PROAPS`, `InCube`, `InSpire`, `InSpireInRad`, `VivaVida`, `PessoasQueTransformam`, `JogoSUS`) — mesmo header/footer; corpo com hero de caso (badges Instituição/Período/Escala/Função/Papel), imagem de capa 21:9, blocos de "Meu papel", métricas, metodologia e resultado.

## Design Tokens
- Cores neutras: `--campo-0:#F5F4F0` (fundo), `--campo-1:#ECEAE3`, `--campo-2:#141414` (texto/preto), `--campo-3:#5A5A5A`, `--campo-4:#B5B2A8`.
- Cores semânticas (6 funções, uma por categoria de caso): `--c-infra:#352A87`, `--c-inter:#6526A5`, `--c-humano:#A61F8C`, `--c-decisao:#E11D4F`, `--c-acao:#F2672A`, `--c-atencao:#E9BD3A`.
- Tipografia: corpo `Mulish`, display `Barlow Semi Condensed` (900/800 uppercase para títulos), mono `JetBrains Mono` (labels, badges, metadados).
- Grid: 12 colunas, `--gutter:24px`, `--margin:64px` (padding lateral das seções), `max-width:1440px`.

## Interactions & Behavior
- Header sticky com nav; menu hambúrguer abaixo de 991px.
- Carrossel de Projetos: `overflow-x:auto` + `scroll-snap-type:x mandatory`, cards de 340px; setas fazem `scrollBy(±364px)` e ficam com opacidade reduzida (não desabilitadas de fato) nas pontas via detecção de `scrollLeft`/`scrollWidth`.
- Responsivo: grid vira 2 colunas (<992px) e 1 coluna (<768px); paddings reduzidos em telas pequenas.
- Acessibilidade: skip-link "Pular para o conteúdo", `focus-visible` com outline, `prefers-reduced-motion` respeitado, `lang="pt-BR"` em todas as páginas, hierarquia de headings corrigida (h1 único por página, sem pular níveis).

## SEO
Cada página tem `<title>`, `meta description`, canonical, Open Graph e Twitter Card próprios, mais `application/ld+json` (schema.org `Person` no hub, `CreativeWork` nas páginas de caso). **Pendência**: as URLs em meta tags/canonical apontam para `evelynsbitencourt.netlify.app` com nomes de arquivo `.dc.html` — ajustar para as URLs reais de produção (ex.: `index.html`, `/proaps` etc.) no deploy.

## Assets
Imagens ainda **não enviadas** — todas as `<img>` referenciam `images/<nome>.jpg` que precisam ser adicionadas ao repositório com os nomes exatos already usados no código (ex.: `images/retrato-hero.jpg`, `images/proj-proaps.jpg`, `images/proaps-cover.jpg`, etc. — ver cada arquivo `.dc.html` para a lista completa por página).

## Accessibility Audit — Fixed in this pass
- Adicionado `lang="pt-BR"` a todas as páginas.
- Corrigida hierarquia de headings nas páginas de projeto (h1 → h4 direto foi normalizado para h1 → h2).
- Todas as imagens já têm `alt` descritivo.

## Accessibility / UX — Open Items (not yet fixed)
- Contraste: texto `--campo-3` (#5A5A5A) sobre `--campo-0` (#F5F4F0) fica próximo do limite AA (~5:1) para texto pequeno — testar com ferramenta de contraste antes do lançamento.
- Carrossel de projetos não tem indicador de teclado dedicado (setas do teclado não navegam os cards) — considerar suporte a `ArrowLeft`/`ArrowRight` com foco.
- O carrossel de Projetos não sinaliza visualmente que há mais conteúdo fora da viewport (sem gradiente de fade na borda direita).
- Legenda do sistema de 6 cores nunca é explicada ao visitante — está implícita, só faz sentido para quem já conhece o sistema.

## Files
Ver arquivos `.dc.html` neste pacote — cada um é uma página HTML autocontida (o wrapper `<x-dc>`/`support.js` é específico do ambiente de design e pode ser removido; extraia apenas o markup entre `<x-dc>` e `</x-dc>` e a lógica de estado equivalente).
