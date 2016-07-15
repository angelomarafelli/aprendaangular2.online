---
layout: default
title: Componentes
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/components/index.md
tweet: "Como utilizar componentes usando Angular 2"
---

_Updated November 16, 2015_

No Angular 2, Componentes are a principal maneira de criar e espeficicar elementos e lógica na página.

usando Angular 1, nós conseguimos isso através de directivas, controllers e $scope. No angular 2, todos esses conceitos
são combinados em componentes.

### Criando um componente

Aqui está um componente simples que renderiza o valor do atributo `name`, e um botão que aciona um método para imprimir o nosso nome para o console:

```javascript
{% raw %}
import { Component } from '@angular/core';

@Component({
  selector: 'my-component',
  template: '<div>Hello my name is {{name}}. <button (click)="sayMyName()">Say my name</button></div>'
})
export class MyComponent {
  constructor() {
    this.name = 'Max'
  }
  sayMyName() {
    console.log('My name is', this.name)
  }
}
{% endraw %}
```

Quando usamos a tag `<my-component></my-componente>` em nosso HTML, este componente será criado, o nosso construtor chamado e renderizado no DOM.
