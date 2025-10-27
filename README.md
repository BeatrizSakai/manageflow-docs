# ManageFlow — Documentação (MkDocs + Material)

## Requisitos
- Python 3.8+
- Git e repositório no GitHub

## Rodar local
```bash
pip install mkdocs mkdocs-material
mkdocs serve
```
Acesse http://127.0.0.1:8000

## Publicar no GitHub Pages
1. Faça commit/push (branch `main`).
2. O workflow cria/atualiza a branch `gh-pages`.
3. Em **Settings → Pages**, selecione `Deploy from a branch` e a branch `gh-pages`.

**URL**: `https://SEU_USUARIO.github.io/manageflow-docs/`

### Domínio próprio (opcional)
- Na branch `gh-pages`, crie um arquivo `CNAME` com: `docs.seudominio.com`
- No DNS, aponte `docs` (CNAME) para `SEU_USUARIO.github.io`.

## Personalização de Marca
- Substitua `docs/assets/logo-light.svg`, `logo-dark.svg` e `favicon.png`.
- Ajuste cores/tipografia em `docs/assets/brand.css`.
