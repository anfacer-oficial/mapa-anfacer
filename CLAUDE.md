# Mapa das Empresas Anfacer

Site estático (HTML + JS, sem build) com o mapa interativo das empresas associadas à Anfacer.
Publicado na Vercel em https://mapa-associados-anfacer.vercel.app e embedado no site da Anfacer (Webflow) por iframe com `?embed=1`.

**Cada push na branch `main` publica o site automaticamente.** Não há etapa de build: o que está no repositório é o que vai ao ar.

## Arquivos

| Arquivo | O que tem | Quando mexer |
|---|---|---|
| `data.js` | Lista `window.EMPRESAS`: uma linha por empresa | Quase sempre: catálogo, fotos, redes, produtos, contatos, empresa nova |
| `index.html` | Layout, estilos, lógica do mapa, filtros e popup | Mudanças visuais ou de comportamento |
| `topo.js` | Contorno simplificado dos estados (reserva caso a API do IBGE falhe) | Nunca |

## Campos de cada empresa (`data.js`)

```js
{
  "id": "almeida",                 // único, minúsculo, sem acento; usado no link #empresa=almeida
  "name": "Almeida",
  "marcas": ["Almeida","Gaudi"],
  "grupo": "Grupo Almeida",
  "segmento": "Placas Cerâmicas",
  "tipos": ["revestimento","porcelanato"],   // revestimento | porcelanato | louca  (filtro "Tipo de produto")
  "producao": ["Via Seca","Via Úmida"],
  "selos": {"porcelanato":true, "sustentavel":false, "psq":true},  // certificados no popup
  "site": "https://...", "email": "...", "tel": "...",
  "logo": "arquivo.jpg",           // nome do arquivo na CDN do Webflow da Anfacer (LOGO_BASE no index.html)
  "foto": "",                      // URL da foto da fábrica (aparece no popup)
  "social": {"whatsapp":"5519...", "instagram":"@usuario", "facebook":"pagina", "linkedin":"empresa"},
  "produtos": [{"titulo":"Coleção X","subtitulo":"Natureza morta","imagem":"URL","url":"URL"}],
  "catalogo": "",                  // URL do catálogo completo (vira um card em "Produtos")
  "locais": [{"city":"Santa Gertrudes","uf":"SP","ibge":"3546702","lat":-22.457,"lon":-47.53}]
}
```

Campos vazios simplesmente não aparecem no popup.

### Adicionar uma cidade nova a uma empresa
`ibge` é o código do município no IBGE (consulte `https://servicodados.ibge.gov.br/api/v1/localidades/estados/{UF}/municipios`).
`lat`/`lon` são as coordenadas do centro da cidade. Sem o código IBGE certo, o município não é destacado ao aproximar o mapa.

## Regras

- Na interface, use sempre **"empresa"**, nunca "associado".
- Paleta: vermelho `#E20A17`, azul `#0078C1`, verde `#00894B`, amarelo `#FDC124`, laranja `#FD7217`. Fonte: Poppins.
- Cores das regiões: Sudeste verde, Sul azul, Nordeste laranja, Centro-Oeste amarelo, Norte vermelho.
- Cores dos tipos: Revestimento azul, Porcelanato verde, Louça laranja.
- Mantenha `data.js` válido: vírgula entre empresas, aspas duplas, sem vírgula depois da última.
- Antes de dar push, abra o `index.html` no navegador (ou rode `npx serve .`) e confira se o mapa carrega sem erro no console.
