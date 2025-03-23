# web-recon-bookmarklets

Coleção de bookmarklets para automação de tarefas de coleta e análise no navegador. Ideal para processos de OSINT, pentest manual e automações em ambientes web.

---

## 🔹 O que são bookmarklets?

Bookmarklets são scripts em JavaScript salvos diretamente como "favoritos" no navegador. Quando clicados, eles executam código diretamente na página que você está visitando.

## 🔹 Como usar

1. Copie o código do arquivo `.js` correspondente.
2. No seu navegador, crie um novo favorito.
3. No campo de URL do favorito, cole o código já com `javascript:(function(){...})();` ao redor.
4. Salve e clique quando estiver em uma página para executar.

## 🔹 Estrutura

### `/bookmarklets`

- `extract-ips.js`: Extrai todos os IPs (IPv4) da página.
- `extract-emails.js`: Extrai todos os emails.
- `extract-links.js`: Coleta todas as URLs (hrefs) da página.
- `extract-phones.js`: Extrai números de telefone.
- `extract-keywords.js`: Coleta palavras-chave com mais de 5 letras.
- `extract-headers.js`: Lista todos os `<h1>`, `<h2>`, etc.
- `extract-forms.js`: Coleta campos de formulário.
- `extract-texts.js`: Baixa todo o texto visível da página.
- `extract-cookies.js`: Exporta cookies da sessão atual.
- `show-hidden-fields.js`: Revela campos ocultos (hidden/display:none).

---

## 🔹 Uso seguro e ético

- Esta coleção é para uso educacional, OSINT e testes em ambientes autorizados.
- Nunca execute scripts em sites sem permissão ou fora de escopo.

## 🔹 Licença

MIT License

---
