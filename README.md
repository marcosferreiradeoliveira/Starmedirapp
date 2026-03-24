# Formulário IR 2025 · StartMedIR

Site estático (`index.html` + jsPDF). A chave **Web3Forms não fica no repositório**: o GitHub Actions injeta o secret só no arquivo publicado.

## GitHub Secrets + Pages (Actions)

1. **Repository → Settings → Secrets and variables → Actions → New repository secret**  
   - Nome: `WEB3_FORMS_ACCESS_KEY`  
   - Valor: a *Access Key* do [web3forms.com](https://web3forms.com) (conta **startmedir@gmail.com**).

2. **Settings → Pages → Build and deployment**  
   - Em **Source**, escolha **GitHub Actions** (não “Deploy from a branch”).  
   - O workflow `.github/workflows/deploy-pages.yml` publica só `_site/index.html` com a chave já substituída.

3. Cada `git push` na `main` dispara o deploy. Na primeira vez, o ambiente **github-pages** pode pedir aprovação em **Actions**.

**Histórico do Git:** se a chave já foi commitada antes, ela ainda aparece em commits antigos — vale **gerar uma chave nova** no Web3Forms, guardar só no secret e (opcional) revogar a antiga.

**Site no ar:** a chave continua visível no JavaScript que o navegador baixa (inevitável para API no front). O que ganhamos é não versionar no código aberto e poder trocar pelo painel do GitHub.

## Web3Forms

- Corpo do e-mail = resumo em texto de todos os campos; PDF continua sendo **download** no aparelho do cliente.
- `tryAttachPdf` tenta anexo; plano gratuito costuma cair no envio só texto (o workflow já trata o fallback no JS).
- Restrinja **domínios** no painel Web3Forms ao seu `*.github.io`.

## Desenvolvimento local

Abra `index.html` no navegador. Enquanto `web3AccessKey` for o placeholder `__WEB3_FORMS_KEY__`, o envio automático não funciona — para testar, substitua temporariamente pela chave (sem commitar) ou rode um `sed` local.

O arquivo `formulario-ir-saude (3).html` é cópia de trabalho; o deploy usa **`index.html`**.
