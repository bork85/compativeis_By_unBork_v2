# Compatíveis — Landing Page

Landing page institucional para o programa de Terapia Ocupacional **Compatíveis**, conduzido por Marcio Conceição. O projeto é uma página estática de apresentação e captação de leads, com foco em clareza emocional e relações saudáveis.

---

## Estrutura do Projeto

```bash
compativeis_v2/
├── index.html       # Estrutura e conteúdo da página
├── styles.css       # Toda a estilização (variáveis, componentes, responsividade)
└── assets/          # Imagens, logo, favicon e fotos de depoimentos
```

> O projeto não usa frameworks nem bundlers — é HTML, CSS e assets puros, sem dependências de build.

---

## Seções da Página

| Seção | ID | Descrição |
| --- | --- | --- |
| Header | — | Logo, navegação e botão de CTA |
| Hero | — | Headline principal e foto do terapeuta |
| Sobre | `#about` | Apresentação e diferenciais da abordagem |
| Metodologia | `#method` | Método 3Rs: Revelar, Romper, Restaurar |
| Trilhas | `#paths` | 5 trilhas de transformação em timeline |
| Depoimentos | `#reviews` | Cards com relatos de pacientes |
| Conteúdo | `#contain` | Encontros ao vivo e comunidade exclusiva |
| Bônus | `#bonus` | Materiais extras inclusos na inscrição |
| Garantia | `#garanty` | Garantia de 7 dias sem risco |
| Footer CTA | — | Chamada final para agendamento |

---

## Dependências Externas (via CDN)

Nenhuma instalação necessária. As dependências são carregadas diretamente no `<head>`:

- **Google Fonts** — `Inter`, `Playfair Display`, `Mrs Saint Delafield`
- **Material Symbols** — ícones do Google (outlined)
- **Font Awesome 6.4** — ícones complementares

---

## Como Rodar Localmente

Por ser um projeto estático, basta abrir o arquivo no navegador:

```bash
# Opção 1 — abrir direto
Clique duas vezes em index.html

# Opção 2 — servidor local com VS Code
Instale a extensão Live Server e clique em "Go Live"

# Opção 3 — servidor local com Python
python -m http.server 3000
# Acesse: http://localhost:3000
```

---

## Arquitetura do CSS

O `styles.css` é organizado em camadas:

1. **Variáveis globais** — cores, tipografia, espaçamentos (`--color-primary`, `--font-sans`, etc.)
2. **Reset e base** — normalização de elementos HTML
3. **Utilitários** — classes atômicas reutilizáveis (`.text-center`, `.mb-4`, `.flex-col`, etc.)
4. **Componentes** — estilização de seções específicas (`.hero-section`, `.card-metodo`, etc.)
5. **Responsividade** — media queries ao final do arquivo

### Breakpoints

| Query | Comportamento |
| --- | --- |
| `min-width: 768px` | Layout desktop: grid de 2 colunas, margens maiores |
| `max-width: 992px` | Layout mobile: coluna única, nav oculta, footer em grid |

### Grid do Footer (mobile)

No mobile, o footer usa `grid-template-areas` para reorganizar os elementos:

```css
footer {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-areas:
    "links links"
    "logo text";
}

/* Nos filhos, sem aspas: */
.links-footer { grid-area: links; }
.logo         { grid-area: logo; }
.text-footer  { grid-area: text; }
```

---

## Assets

| Arquivo | Uso |
| --- | --- |
| `logo.webp` | Logo no header e footer |
| `favicon.png` | Ícone da aba do navegador |
| `hero-marcio.png` | Foto do terapeuta na seção hero |
| `sobre.png` | Imagem da seção Sobre |
| `encontros.png` | Card de encontros ao vivo |
| `comunidade.png` | Card de comunidade exclusiva |
| `trilhas.png` | Imagem da seção de trilhas |
| `selo-garantia-7-dias-small.png` | Selo de garantia |
| `footer-escuro.jpg` / `footer-claro.jpg` | Background do footer CTA |
| `user1-3.jpg` | Fotos dos depoimentos |

---

## Deploy

Por ser um projeto estático, pode ser publicado em qualquer serviço de hospedagem de arquivos:

- **AWS S3 + CloudFront** — hospedagem estática com CDN global
- **Netlify / Vercel** — deploy via drag-and-drop ou Git
- **GitHub Pages** — gratuito para repositórios públicos

Para o S3, o fluxo básico é:

```bash
aws s3 sync . s3://<nome-do-bucket> --exclude ".git/*"
```

>Para este projeto foi escolhido o Github Pages pela facilidade <https://bork85.github.io/compativeis_By_unBork_v2/>
---

## Contato e Agendamento

O botão de CTA aponta para um formulário externo via [respondi.app](https://respondi.app). Para alterar o link de agendamento, busque por `form.respondi.app` no `index.html`.
