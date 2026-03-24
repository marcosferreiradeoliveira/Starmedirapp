# Formulário IR 2025 · StartMedIR

Site estático (`index.html`). A **Access Key do Web3Forms** está em `FORM_CONFIG.web3AccessKey` no código (é tratada como id público do formulário). No painel [web3forms.com](https://web3forms.com), restrinja **domínios** ao seu `*.github.io`.

## GitHub Pages (Actions)

1. **Settings → Pages → Source:** **GitHub Actions**
2. Cada `git push` na `main` roda `.github/workflows/deploy-pages.yml` e publica `_site/index.html`.

O e-mail que recebe as notificações é o da conta Web3Forms da chave; no código, `NOTIFICATION_EMAIL` deve bater com esse uso (ex.: **startmedir@gmail.com**).

## Desenvolvimento local

`RELAXED_VALIDATION = true` libera avançar sem obrigatórios (testes). Para produção, use `false`.

O arquivo `formulario-ir-saude (3).html` é cópia do `index.html`; o deploy usa **`index.html`**.
