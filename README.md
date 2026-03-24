# Formulário IR 2025 · StartMedIR

Site estático (um único HTML + jsPDF). Pode ser publicado no **GitHub Pages** sem backend próprio.

## Enviar respostas para `startmedir@gmail.com`

Páginas estáticas **não enviam e-mail sozinhas**. Este projeto usa **[Web3Forms](https://web3forms.com)** (grátis para começar): o navegador faz um `POST` para a API deles e eles encaminham o conteúdo para o e-mail cadastrado na chave.

### Configuração rápida

1. Acesse [web3forms.com](https://web3forms.com), crie uma chave (**Access Key**) usando o e-mail **startmedir@gmail.com** (é para lá que as notificações chegam).
2. Abra `index.html` (ou o arquivo do formulário) e localize no `<script>`:

   ```javascript
   const FORM_CONFIG = {
     web3AccessKey: '',
     tryAttachPdf: true
   };
   ```

3. Cole a chave em `web3AccessKey: 'SUA_CHAVE_AQUI'`, salve e faça o deploy.
4. No painel do Web3Forms, restrinja **domínios permitidos** ao seu site (ex.: `seudominio.github.io`) para reduzir abuso da chave exposta no HTML.

**PDF anexo:** no Web3Forms, anexo costuma ser **recurso pago**. Com plano gratuito, o e-mail recebe **todo o texto do formulário** no corpo; o PDF continua sendo **baixado** no computador/celular do cliente. Se `tryAttachPdf: true` e o plano não permitir anexo, o código tenta de novo **só com texto**.

### Privacidade

O corpo do e-mail inclui dados sensíveis (incluindo credenciais Gov.br, como já estava no PDF). Ao usar Web3Forms, esses dados passam pelos servidores deles. Para máximo controle, alternativa é um **Google Apps Script** ou função serverless própria (fora do escopo deste repositório).

## GitHub Pages

1. Crie um repositório no GitHub e envie estes arquivos (no mínimo `index.html`).
2. **Settings → Pages → Build and deployment → Branch** → escolha `main` e pasta **`/ (root)`** (ou `docs/` se colocar o HTML lá).
3. Após o build, o site ficará em `https://<usuario>.github.io/<repo>/`.

Confirme que `index.html` está na raiz (ou na pasta que o Pages usa). O arquivo `formulario-ir-saude (3).html` é cópia legada; o deploy pode usar só `index.html`.

## Teste local

Abra `index.html` no navegador. Para o envio Web3Forms funcionar, é preciso de **internet** e uma chave válida.
