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
### /bookmarklets/extract-ips.js
```javascript
var ips=[];document.querySelectorAll("body *").forEach(function(e){var txt=e.innerText;var ipMatch=txt.match(/\b\d{1,3}(\.\d{1,3}){3}\b/g);if(ipMatch)ips=ips.concat(ipMatch);});var uniqueIps=[...new Set(ips)];var ipString=uniqueIps.join("\n");var a=document.createElement("a");a.href="data:text/plain;charset=utf-8,"+encodeURIComponent(ipString);a.download="ips.txt";document.body.appendChild(a);a.click();document.body.removeChild(a);
```

### /bookmarklets/extract-emails.js
```javascript
var emails=[];document.querySelectorAll("body *").forEach(function(e){var txt=e.innerText;var match=txt.match(/[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}/g);if(match)emails=emails.concat(match);});var unique=[...new Set(emails)];var str=unique.join("\n");var a=document.createElement("a");a.href="data:text/plain;charset=utf-8,"+encodeURIComponent(str);a.download="emails.txt";document.body.appendChild(a);a.click();document.body.removeChild(a);
```

### /bookmarklets/extract-links.js
```javascript
var links=[];document.querySelectorAll("a").forEach(function(e){if(e.href)links.push(e.href);});var linkString=links.join("\n");var a=document.createElement("a");a.href="data:text/plain;charset=utf-8,"+encodeURIComponent(linkString);a.download="links.txt";document.body.appendChild(a);a.click();document.body.removeChild(a);
```

### /bookmarklets/extract-phones.js
```javascript
var phones=[];document.querySelectorAll("body *").forEach(function(e){var txt=e.innerText;var match=txt.match(/(\(?\d{2,3}\)?\s?\d{4,5}[-\s]?\d{4})/g);if(match)phones=phones.concat(match);});var unique=[...new Set(phones)];var str=unique.join("\n");var a=document.createElement("a");a.href="data:text/plain;charset=utf-8,"+encodeURIComponent(str);a.download="phones.txt";document.body.appendChild(a);a.click();document.body.removeChild(a);
```

### /bookmarklets/extract-keywords.js
```javascript
var words=[];document.querySelectorAll("body *").forEach(function(e){var txt=e.innerText;var match=txt.match(/\b[a-zA-Z]{5,}\b/g);if(match)words=words.concat(match);});var unique=[...new Set(words)];var str=unique.join("\n");var a=document.createElement("a");a.href="data:text/plain;charset=utf-8,"+encodeURIComponent(str);a.download="keywords.txt";document.body.appendChild(a);a.click();document.body.removeChild(a);
```

### /bookmarklets/extract-headers.js
```javascript
var headers=[];document.querySelectorAll("h1,h2,h3,h4,h5,h6").forEach(function(e){headers.push(e.innerText.trim());});var str=headers.join("\n");var a=document.createElement("a");a.href="data:text/plain;charset=utf-8,"+encodeURIComponent(str);a.download="headers.txt";document.body.appendChild(a);a.click();document.body.removeChild(a);
```

### /bookmarklets/extract-forms.js
```javascript
var inputs=[];document.querySelectorAll("input,textarea,select").forEach(function(e){inputs.push(e.tagName + " - name: " + (e.name||'') + ", type: " + (e.type||'') + ", placeholder: " + (e.placeholder||''));});var str=inputs.join("\n");var a=document.createElement("a");a.href="data:text/plain;charset=utf-8,"+encodeURIComponent(str);a.download="inputs.txt";document.body.appendChild(a);a.click();document.body.removeChild(a);
```

### /bookmarklets/extract-texts.js
```javascript
var texts=[];document.querySelectorAll("body *").forEach(function(e){if(e.innerText)texts.push(e.innerText.trim());});var str=texts.join("\n");var a=document.createElement("a");a.href="data:text/plain;charset=utf-8,"+encodeURIComponent(str);a.download="page-texts.txt";document.body.appendChild(a);a.click();document.body.removeChild(a);
```

### /bookmarklets/extract-cookies.js
```javascript
var cookies=document.cookie;var a=document.createElement("a");a.href="data:text/plain;charset=utf-8,"+encodeURIComponent(cookies);a.download="cookies.txt";document.body.appendChild(a);a.click();document.body.removeChild(a);
```

### /bookmarklets/show-hidden-fields.js
```javascript
document.querySelectorAll('[type="hidden"],[style*="display:none"]').forEach(function(e){e.style.display="block";e.type="text";});alert('Campos ocultos revelados!');
```

---
