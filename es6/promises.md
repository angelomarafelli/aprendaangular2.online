---
layout: default
title: Promises
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/es6/promises.md
tweet: "Pomises no Angular 2"
---

_Atualizado em 16 de Julho de 2016_

Promises permite escrever código assincrono de maneira mais fácil, comparanda por exemplo ao o uso de callbacks. Muitas bibliotecas e Web APIs retornam promessas para operações assíncronas, como `fetch()`:

```javascript
loadUsers() {
  fetch('/api/usuarios').then((response) => {
    return response.json();
  }).then((data) => {
    this.users = data;
  }).catch((ex) => {
    console.error('Erro: usuários não puderam ser listados', ex);
  });
}
```

Nós também podemos riar nossas próprias promessas usando o construtor `new Promise()`, porém isso deve ser evitado se você utiliza alguma biblioteca ou framework que já possui uma API como o `fetch()`:

```javascript
respostaDaVidaDoUniversoETudoMais() {
  return new Promise((resolve, reject) => {
    resolve(42);
  });
}
```

Promises parecem simples a um primeiro moemnto, mas são complexas e extremamente poderosas na prática. Se ligue para não vacilar e fazer [anti-patterns](http://www.datchley.name/promise-patterns-anti-patterns/) no seu código.
