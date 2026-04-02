# Workflow de Propostas V4 Bilinski

Processo padrao para criar propostas comerciais personalizadas a partir do template master.

---

## Estrutura do Repositorio

```
propostas-bilinski/
├── index.html                    # Demo/showcase (raiz)
├── _template/
│   ├── master.html               # Template master (NAO EDITAR)
│   ├── client-config.json        # Skeleton de configuracao
│   └── README.md                 # Instrucoes rapidas
├── {nome-cliente}/               # Proposta personalizada
│   ├── index.html
│   └── client-config.json
├── data/                         # Dados de produtos
├── prd/                          # PRD e documentacao
├── stories/                      # User stories
└── deliverables/                 # Historico de entregas
```

## URLs

| Conteudo | URL |
|----------|-----|
| Demo | `v4bilinski.github.io/propostas-bilinski/` |
| Cliente | `v4bilinski.github.io/propostas-bilinski/{nome-cliente}/` |

---

## 6 Passos para Nova Proposta

### Passo 1 — Criar pasta do cliente

```bash
mkdir {nome-cliente}
```

**Convencao:** lowercase, hifen, sem acentos. Ex: `acme-corp`, `mwm-latam`

### Passo 2 — Criar client-config.json

Copiar de `_template/client-config.json` e preencher:

- `client.name` — Nome da empresa
- `client.logo_url` — URL ou base64 do logo
- `client.primary_color` — Cor primaria (hex)
- `client.website` — Site do cliente
- `client.whatsapp` — WhatsApp para contato
- `study.title` — Titulo da proposta
- `study.subtitle` — Subtitulo descritivo
- `hero_stats` — 3 metricas do hero

### Passo 3 — Gerar o HTML

1. Copiar `_template/master.html` para `{nome-cliente}/index.html`
2. Substituir CSS variable `--red` com `primary_color` do cliente (Fases B e C)
3. Substituir logo do cliente na nav
4. Atualizar `<title>` e `<meta description>`
5. Atualizar hero (titulo, subtitulo, badge, stats)
6. Atualizar Fase B com dados do produto (de `data/product-delivery-template.json` ou custom)
7. Atualizar links WhatsApp e website nos CTAs
8. Revisar acentos e ortografia em portugues

### Passo 4 — Validar

- [ ] Acordeoes abrem/fecham corretamente
- [ ] Animacoes funcionam (scroll reveal, counters, glow)
- [ ] Responsivo no mobile
- [ ] Acentos corretos em todo o texto
- [ ] Links funcionam (WhatsApp, website)
- [ ] Logos renderizam corretamente

### Passo 5 — Deploy

```bash
git add {nome-cliente}/
git commit -m "feat: adicionar proposta para {Nome Empresa}"
git push origin main
```

Deploy automatico via GitHub Actions. Proposta fica live em:
`https://v4bilinski.github.io/propostas-bilinski/{nome-cliente}/`

### Passo 6 — Compartilhar

Enviar a URL diretamente ao cliente. Nenhuma acao adicional necessaria.

---

## Atualizando o Template Master

Quando o template base precisar de alteracoes:

1. Editar `_template/master.html`
2. Copiar para `index.html` (demo na raiz)
3. Commit e push
4. **Propostas existentes NAO sao afetadas** (snapshot point-in-time)

---

## Referencia

- PRD completo: `prd/PRD-market-research-page.md`
- Dados do produto: `data/product-delivery-template.json`
- Story original: `stories/1.1.story.md`
