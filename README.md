# Mapa das Empresas Anfacer

Mapa interativo das empresas associadas à Anfacer, por região, estado e cidade.

- Site: https://mapa-associados-anfacer.vercel.app
- Embed no Webflow: `https://mapa-associados-anfacer.vercel.app/?embed=1` (esconde o topo verde)
- Link direto para uma empresa: `https://mapa-associados-anfacer.vercel.app/#empresa=almeida`

## Como editar

Cada alteração salva na branch `main` é publicada automaticamente na Vercel em cerca de 1 minuto.

- **Conteúdo das empresas** (catálogo, fotos, redes sociais, produtos, contatos): arquivo `data.js`.
- **Layout e comportamento:** arquivo `index.html`.

Com o Claude, é só conectar o GitHub e pedir, por exemplo:
"No repositório mapa-anfacer, coloca o link do catálogo da Portobello: https://..."

As instruções completas para o Claude estão em `CLAUDE.md`.

## Créditos dos dados

- Empresas: cadastro Anfacer.
- Contornos de estados e municípios: API de malhas do IBGE (carregada em tempo real).
- Logos: site da Anfacer.
