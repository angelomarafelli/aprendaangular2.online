---
layout: default
title: Arrow Functions
edit_link: https://github.com/joselitojunior1/aprenda-angular2/edit/gh-pages/es6/arrow-functions.md
tweet: "Arrow Functions ES6/TypeScript"
---

Arrow functions permitem um jeito fácil de criar funções anonimas, e também de fazer `bind` no context atual. Veja o exemplo a seguir:

```javascript
class Peessoa {
  constructor() {
    this.name = 'Jose';

    setTimeout(() => {
      // Isso imprime "Jose" no console, pois foi feito o bind automáticamente do this para o contexto atual
      console.log(this.name);
    });
  }
}
```

É equivalente a fazer:

```javascript
var _this = this;
setTimeout(function() {
  console.log(_this.name);
});
```

Mas de um jeito muito mais limpo.

PS: Nós não traduzimos Arrow Functions por opção. Mas queremos discutir se devemos. Vem conversar com a gente nessa [issue](https://github.com/joselitojunior1/aprenda-angular2/issues/1)
