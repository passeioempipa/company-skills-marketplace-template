# company-skills-marketplace-template

Marketplace de plugins do Claude Code com o kit usado nos sites dos clientes.

| Plugin | O que traz | Origem |
|---|---|---|
| `agencia-kit` | `/agencia-kit:novo-cliente` — lê o site e gera a brand-guidelines, o `product-marketing.md` e o `.claude/settings.json` do cliente | Este repositório |
| `marketing-skills` | 50 skills de marketing: `ai-seo`, `seo-audit`, `schema`, `copywriting`, `content-strategy`… | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) (MIT) |
| `content-ideas` | Pesquisa de concorrentes nas redes e ideias de conteúdo (precisa de chave ScrapeCreators) | [bradautomates/content-ideas](https://github.com/bradautomates/content-ideas) (MIT) |

Os plugins de terceiros ficam **fixados num commit revisado** (`sha` em `.claude-plugin/marketplace.json`). Para atualizar, revise o que mudou no repositório original e troque o `sha`.

## Usar num site de cliente

Dentro do repositório do cliente, numa sessão do Claude Code:

```
/plugin marketplace add passeioempipa/company-skills-marketplace-template
/plugin install agencia-kit@agencia
/agencia-kit:novo-cliente
```

A skill `novo-cliente` gera a identidade do cliente e grava em `.claude/settings.json` o marketplace e os plugins ativados. Depois de commitar esse arquivo, toda sessão nova naquele repositório já carrega o kit.

Instalação manual dos outros plugins:

```
/plugin install marketing-skills@agencia
/plugin install content-ideas@agencia
```

## Acesso a repositório privado

O Claude Code clona o marketplace com o `git` da máquina, sem pedir senha. Se este repositório for privado, a máquina precisa já ter credencial do GitHub (`gh auth login` + `gh auth setup-git`, ou chave SSH). Em sessões do Claude Code na nuvem, se o marketplace não carregar, deixe este repositório público — ele não contém dados de clientes — ou rode `/agencia-kit:novo-cliente` a partir de uma máquina com acesso e copie as skills para `.claude/skills/` do cliente.

## Adicionar uma skill própria

1. Crie `plugins/agencia-kit/skills/<nome>/SKILL.md` (frontmatter com `name` e `description`).
2. `claude plugin validate .`
3. Commit e push. Quem usa roda `/plugin marketplace update agencia` (ou ativa a atualização automática em `/plugin` → Marketplaces).
