---
layout: default
title: ES6 Template Strings
edit_link: https://github.com/joselitojunior1/aprenda-angular2/edit/gh-pages/es6/template-strings/index.md
tweet: "Usando ES6 Template Strings"
---

ES6 adiciona a possiblidade de escrever uma string em várias linhas, sem tem que fazer aquele concatenamento terrível. Tudo que a gente precisa é usar backticks (o acento grave) no início e no fim da string:

```html
let template = `
  <div>
    <h2>Malandramente</h2>
    <h3>Mc Nandinho (Part. Mc Nego Bam)</h3>
    <p>Malandramente</p>
  
    <p>
      A menina inocente<br>
      Se envolveu com a gente<br>
      Só pra poder curtir
    </p>
  </div>
`;
```

A gnete agora consegue até fazer interpolação de uma expressão, usando `${expression}`:

```html
let x = 5;
let y = 10;
let template = `
  <div>O valor da soma é <span>${ x + y }</span></div>
`;
```
