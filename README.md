# Formulário IR 2025 · StartMedIR

Site estático (`index.html`). A chave **Web3Forms não fica no repositório**: o GitHub Actions injeta o secret só no arquivo publicado.

## GitHub Secrets + Pages (Actions)

1. **Repository → Settings → Secrets and variables → Actions → New repository secret**  
   - Nome: `WEB3_FORMS_ACCESS_KEY`  
   - Valor: a *Access Key* do [web3forms.com](https://web3forms.com).

2. A **Access Key deve estar cadastrada no mesmo e-mail** definido em `NOTIFICATION_EMAIL` no `index.html` (hoje `marcosfoliveira@gmail.com` para testes). Quem recebe a notificação é sempre a conta da chave no Web3Forms.

3. **Settings → Pages → Build and deployment**  
   - Em **Source**, escolha **GitHub Actions**.  
   - O workflow `.github/workflows/deploy-pages.yml` publica `_site/index.html` com a chave já substituída.

4. Cada `git push` na `main` dispara o deploy.

**Site no ar:** a chave continua no JavaScript baixado pelo navegador (típico de formulário 100% no front). Restrinja **domínios** no painel Web3Forms.

## Desenvolvimento local

`RELAXED_VALIDATION = true` libera avançar sem obrigatórios (testes). Para produção, use `false`.

Enquanto `web3AccessKey` for `__WEB3_FORMS_KEY__`, use deploy com secret ou substitua localmente sem commitar.

O arquivo `formulario-ir-saude (3).html` é cópia do `index.html`; o deploy usa **`index.html`**.
