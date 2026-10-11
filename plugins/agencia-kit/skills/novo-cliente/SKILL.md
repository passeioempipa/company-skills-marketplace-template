---
name: novo-cliente
description: Prepara o repositório do site de um cliente para trabalhar com o Claude — lê o código e os textos do site e gera a skill de identidade de marca (.claude/skills/brand-guidelines), o contexto de marketing (.claude/product-marketing.md) e a configuração que ativa o kit da agência (.claude/settings.json). Use quando o usuário pedir para "configurar um cliente novo", "preparar este site", "criar a brand guidelines / identidade / manual de marca do cliente", "gerar o product-marketing", ou atualizar esses arquivos depois de mudanças no site.
---

# Novo cliente

Transforma o que já existe no site do cliente em três arquivos que as outras skills usam. **Tudo sai do código e dos textos do site ou do que o usuário disser — nunca invente** cores, números, credenciais, avaliações, prêmios ou concorrentes. O que não estiver no site fica marcado como **(a preencher)** e vira pergunta no final.

Escreva em português do Brasil, a menos que o site seja em outro idioma.

## 1. Levantar o material

Leia, nesta ordem, o que existir no repositório:

1. **Tema visual:** CSS global (`src/styles.css`, `app/globals.css`, `src/index.css`…), `tailwind.config.*`, blocos `@theme`, variáveis CSS (`--color-*`, `--primary`…), tokens de design, `components.json`.
2. **Fontes:** imports do Google Fonts / `next/font` / `@fontsource`, `font-family` nas regras base.
3. **Componentes de marca:** classes utilitárias próprias (botões, títulos, rótulos), raio de borda, sombras, animações e se respeitam `prefers-reduced-motion`.
4. **Conteúdo e dados:** arquivos de dados/constantes (contato, serviços, FAQ, depoimentos), componentes de seção (hero, sobre, serviços, CTA, rodapé), posts do blog.
5. **SEO existente:** `public/llms.txt`, `robots.txt`, sitemap, metatags e schema no layout raiz.
6. **Imagens e logo:** nomes e `alt` dos assets.
7. Instruções do repositório (`AGENTS.md`, `CLAUDE.md`) — respeite-as.

Se `.claude/product-marketing.md` ou `.claude/skills/brand-guidelines/SKILL.md` já existirem, **atualize** preservando o que o usuário escreveu à mão, em vez de sobrescrever.

## 2. Gerar `.claude/skills/brand-guidelines/SKILL.md`

Use o modelo em [references/brand-guidelines-template.md](references/brand-guidelines-template.md). Regras:

- Paleta: só cores que existem no código, com hex e nome do token. Calcule o contraste de texto sobre fundo para indicar qual cor serve para texto pequeno (WCAG AA ≥ 4,5:1) e registre isso.
- Tipografia: fontes reais do site + fallbacks para Word/PowerPoint/Canva.
- Tom de voz: descreva a partir dos textos reais e cite 2–4 frases do próprio site como exemplo.
- `description` do frontmatter: comece com o nome do cliente e cubra os gatilhos (criar/alterar páginas, posts, artes, apresentações, e-mails; "marca", "identidade", "tom de voz").
- Inclua a seção de regras do setor (passo 4).

## 3. Gerar `.claude/product-marketing.md`

Use o modelo em [references/product-marketing-template.md](references/product-marketing-template.md). É o arquivo que as skills do plugin `marketing-skills` (ai-seo, seo-audit, copywriting…) leem antes de fazer perguntas. Indique de quais arquivos do repositório cada informação veio.

## 4. Regras do setor

Identifique o setor do cliente e registre, nos dois arquivos, as restrições de publicidade que se aplicam. Para profissões regulamentadas no Brasil (odontologia — CFO; medicina — CFM; advocacia — OAB; psicologia — CFP; nutrição — CFN; fisioterapia — COFFITO; imóveis — CRECI; contabilidade — CFC…), anote os pontos gerais (registro profissional visível, sem promessa de resultado, sem sensacionalismo, regras sobre preços, depoimentos e antes/depois) e marque **"confirmar com o cliente as normas vigentes do conselho"** — as resoluções mudam e você não deve afirmar um detalhe normativo que não verificou.

## 5. Configurar `.claude/settings.json`

Garanta que o arquivo tenha o marketplace da agência e os plugins ativados, mesclando com o que já existir (não apague outras chaves):

```json
{
  "extraKnownMarketplaces": {
    "agencia": {
      "source": { "source": "github", "repo": "passeioempipa/company-skills-marketplace-template" }
    }
  },
  "enabledPlugins": {
    "agencia-kit@agencia": true,
    "marketing-skills@agencia": true
  }
}
```

Ative `content-ideas@agencia` só se o usuário pedir (ele precisa de chave de API da ScrapeCreators e guarda dados fora do repositório).

## 6. Fechar

1. Mostre um resumo do que foi gerado e de onde veio cada parte.
2. Liste as perguntas para os itens **(a preencher)** (buscas prioritárias, concorrentes, público, diferenciais, normas do conselho).
3. Se o repositório estiver conectado a uma ferramenta como Lovable, avise que a pasta `.claude/` aparecerá lá, sem afetar o site.
4. Commit e push só se o usuário pedir ou se as instruções da sessão mandarem.
