# Instruções para o Claude Code: Cafés Gelados TOSTES

Este é o site de cafés gelados da cafeteria TOSTES&CO (Fazenda Rio Grande, PR). Ele é hospedado no GitHub Pages.

## Regras do projeto
- O site é estático: HTML, CSS e JS puro. Não use framework, build, npm nem bibliotecas externas além do Google Fonts.
- Mudanças de cardápio (preço, bebida nova, texto, ordem) são feitas só em `bebidas.js`. Não coloque dados de bebida em `app.js`.
- Preços sempre com centavos (`17.00`). Na tela eles aparecem como R$ 17,00.
- Grafia: "matcha", sem acento.
- Textos em tom profissional e direto, sem frases de efeito.
- Mobile-first: teste em 360–430 px de largura. A tela deitada e o computador usam o layout lado a lado.
- Não existe seletor geral de açúcar. Escolhas por bebida ficam em `opcoes` (hoje: Chocochoco Sem/Com café; Iced Americano, Long Black e Espresso Tônica Sem/Com açúcar).
- Fotos novas: recorte com fundo transparente, salve como `.webp` com 900 px de altura em `img/` e ajuste os pontos de `anatomia` (`y` e `x`, de 0 a 1) para cada camada da foto.
- Cada bebida tem identidade própria: fonte do nome, fundo (`fundo`) e efeito (`efeito`). Ao criar uma nova, escolha uma fonte que ainda não seja usada e inclua essa fonte no link do Google Fonts no `index.html`.
- O My Lady Latte é uma homenagem à Priscila Tostes (campo `homenagem`). Não remova sem pedir.

- **Versão dos arquivos:** a cada publicação, trocar o `?v=` dos links de `styles.css`, `bebidas.js` e `app.js` no `index.html` (ex.: `?v=20261115c`). Sem isso, o celular mistura a página nova com estilo e código antigos guardados em cache.

## Estrutura do app.js
- O palco usa uma fileira por categoria, sem giro contínuo. A troca acontece por setas, deslize ou toque.
- Os efeitos do fundo ficam num canvas: o objeto `FX` e a função `fxStep`. Para criar um efeito novo, adicione ali e documente no `LEIA-ME.md`.
- A anatomia é feita por `openTags` e `closeTags`.
- O carrinho **nunca é salvo** (cada visita começa vazia, e chaves antigas do localStorage são apagadas) e é esvaziado depois de tocar em enviar. O pedido vai para o WhatsApp via `wa.me`.
- A abertura com nevasca (função `intro`) aparece em toda visita e só fecha no botão "Entrar no frio" (ou Enter/Esc no teclado).
- "Surpreenda-me" (botão no topo do palco): roleta com os copos girando (`sortear`/`revela`), sorteia qualquer bebida diferente da atual e, em "Quero esse!", leva a vitrine até ela (`irPara`). Depois de parar, o "Toque aqui" pulsando no copo e o botão "Toque aqui e veja o que vai" mostram a anatomia da bebida sorteada dentro do cartão (`anaRoleta`, que usa a mesma `montaAnatomia` da vitrine).
