# Modelo — brand-guidelines do cliente

Copie a estrutura abaixo para `.claude/skills/brand-guidelines/SKILL.md` e preencha com o que o site realmente usa. Remova seções que não se aplicam; não deixe placeholders `{{…}}` no arquivo final.

```markdown
---
name: brand-guidelines
description: Aplica a identidade visual e o tom de voz de {{NOME DO CLIENTE}} ({{o que faz, cidade}}) — cores, tipografia, componentes, fotografia e escrita. Use sempre que criar ou alterar seções, páginas, posts do blog, artes para redes sociais, apresentações, documentos, e-mails ou qualquer material de {{NOME}}, ou quando o pedido mencionar marca, identidade visual, paleta, fontes, estilo, tom de voz ou "deixar com a cara do site".
---

# Identidade da marca — {{NOME}}

{{Uma ou duas frases sobre a personalidade visual: ex. "sóbria e acolhedora; navy + dourado discreto; muito respiro".}}

**Fonte da verdade:** {{arquivos de tema e de dados}}. Se este arquivo divergir do código, o código vence — e atualize este arquivo.

## Cores

| Token | Hex | Uso |
|---|---|---|
| {{token}} | {{#hex}} | {{onde aparece no site}} |

Regras:
- {{proporção: cor dominante, estrutura, acento}}
- {{qual cor NÃO usar para texto pequeno e qual usar no lugar, com o contraste}}
- No código, use os tokens, nunca hex solto. Não introduzir cores novas sem pedido.

## Tipografia

- **Títulos:** {{fonte, pesos, ajustes}} — fallback {{Georgia/Arial…}}
- **Texto e interface:** {{fonte, pesos}} — fallback {{…}}
- {{classes utilitárias de título/rótulo, se houver}}

## Componentes e layout

- {{botão principal: classe, cores, raio, altura}}
- {{CTA padrão: destino (WhatsApp/formulário/telefone) e textos usados}}
- {{raio de cantos, bordas, espaçamento, largura de leitura}}
- {{animações e acessibilidade: reduced-motion, foco visível, alt}}

## Fotografia e imagens

- {{estilo das fotos reais do site}}
- {{o que evitar}}
- Logo: {{caminho}} — não distorcer, não recolorir, manter área de respiro.

## Tom de voz

- {{3–4 adjetivos e como isso aparece na escrita}}
- {{tratamento: você/senhor(a); comprimento de frase; jargão}}
- Palavras da marca: {{…}}
- Exemplos do site:
  - "{{frase real}}"
- Evitar: {{superlativos, urgência artificial, promessas, gírias…}}

## Regras obrigatórias ({{setor/conselho}})

- {{registro profissional visível, se houver}}
- {{restrições de publicidade do setor}}
- Depoimentos só se forem reais e conferidos.
- Não inventar números, títulos, prêmios ou credenciais.
- Confirmar com o cliente as normas vigentes do conselho.

## Checklist antes de entregar

1. Só cores da paleta, via tokens.
2. Fontes corretas.
3. Contraste AA em texto pequeno.
4. CTA correto e um principal por bloco.
5. Tom de voz e regras do setor respeitados.
6. Funciona no celular e é acessível.
```
