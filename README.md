# Portfólio — Evelyn Bitencourt

Site estático. Não tem build, não tem dependência de npm. Abrir `index.html` no navegador já funciona.

## Estrutura

    index.html                    home (hero, sobre, carrossel de projetos, contato)
    PROAPS.html                   Programa de fortalecimento em saúde mental na APS
    VivaVida.html                 Mapeamento Viva Vida (mestrado FAUUSP)
    InCube.html                   Programa In.cube, 5 edições
    InSpire.html                  Programa In.spire, projetos de melhoria
    InSpireInRad.html             Discovery do agendamento de exames de imagem
    PessoasQueTransformam.html    Programa de melhoria de serviços públicos (PMSP)
    JogoSUS.html                  Jogo In.spire SUS
    support.js                    runtime das páginas — não editar
    images/                       imagens (ver images/LEIA-ME.txt)
    sitemap.xml, robots.txt       SEO

## Publicar

**Netlify (arrastar):** netlify.com/drop → arraste a pasta inteira.

**Netlify + GitHub:** suba esta pasta como raiz do repositório e conecte.
Build command: deixar vazio. Publish directory: `/` (ou `site` se subir o projeto todo).

**GitHub Pages:** Settings → Pages → Deploy from a branch → `main` / `root`.

Domínio configurado: https://evelynsbitencourt.netlify.app/

## Antes de publicar

- [ ] Colocar as 14 imagens em `images/` (ver LEIA-ME.txt lá dentro)
- [ ] Conferir o e-mail de contato no rodapé
- [ ] Atualizar `<lastmod>` no sitemap.xml se for muito depois de agosto/2026

## Como editar textos

Todo o conteúdo está no HTML de cada página, em português, com marcadores de seção
(`§ Problema`, `§ Decisão`, `§ Resultado`). Estilos são inline, não há CSS separado:
para mudar um texto, procure a frase no arquivo e troque. Para trocar uma imagem,
troque o arquivo em `images/` mantendo o nome.

### Sistema visual

Cores, tipografia e grid estão definidos como variáveis CSS no topo de cada arquivo,
dentro do bloco `<style>`. Os nomes seguem o sistema Field:

    --campo-0/1/2/3/4    neutros, do claro ao escuro
    --c-acao             laranja  · ação
    --c-atencao          amarelo  · atenção / destaque
    --c-humano           verde    · dimensão humana
    --c-infra            azul     · infraestrutura
    --c-inter            roxo     · intermediação
    --c-decisao          vermelho · decisão / alerta
    --ff-display         Barlow Semi Condensed  (títulos)
    --ff-mono            JetBrains Mono         (rótulos, metadados)
    --margin / --gutter  grid de 12 colunas

Mudar uma cor em um arquivo muda só aquela página — as variáveis são repetidas em cada
uma para que qualquer página funcione sozinha.
