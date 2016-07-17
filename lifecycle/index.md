---
layout: default
title: Lifecycle de uma aplicação Angular 2
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/lifecycle/index.md
tweet: "Lifecycle de uma aplicação Angular 2"
---

_Atualizado em 16 de Julho de 2016_

Aplicações Angular passam por um processo várias etapas desde o seu bootstrap e ciclo de vida, podendo
responder a vários eventos como o quando o aplicativo é iniciado, executado e quando se cria/destrói componentes.

## Bootstrap

O Angulares 2 (atualmente) precisa ser inicializado usando o componente de raiz para o aplicativo.

No arquivo JS principal da nossa aplicação, vamos colocar isso:


```javascript
{% raw %}
import { bootstrap } from '@angular/platform-browser-dynamic';
import { Component } from '@angular/core';

// Annotation section
@Component({
  selector: 'my-app',
  template: '<h1>Hello {{ name }}</h1>'
})
// Component controller
class MyApp {
  constructor() {
    this.name = 'Max';
  }
}

bootstrap(MyApp)
{% endraw %}
```

O componente `my-app` inicializa a nossa aplicação em um nível configurável, e seu modelo
é o lugar onde todos os nossos componentes são criados.
nt chain gets created.

## Inicializando o nosso Componente

Quando um componente é criado, seu construtor é chamado. Isto acontece quando inicializamos algum estados
para o nosso componente, mas se baseado em algumas propriedades ou dados de componentes filhos, precisamos
esperar pelos componentes filhos para que o componente inicialize pela primeira vez.

Para fazer isso, nós podemos manipular o evento ciclo de vida utilizando o método `ngOnInit`. Existe a opção de utilizar `setTimeout` em nosso construtor para um efeito semelhante:

```javascript
import {Component, bootstrap} from 'angular2/angular2';

// Annotation section
@Component({
  selector: 'street-map',
  template: '<map-window></map-window><map-controls></map-controls>'
})
// Component controller
class StreetMap {
  constructor() {
    this.name = 'Max';
  }

  setMapWindow(mapWindow) {
    this.mapWindow = mapWindow;
  }

  setMapControls(mapControls) {
    this.mapControls = mapControls;
  }

  ngOnInit() {
    // Properties are resolved and things like
    // this.mapWindow and this.mapControls
    // had a chance to resolve from the
    // two child components <map-window> and <map-controls>
  }
}
```

## Ciclo de vida de um componente

Como `ngOnInit`, podemos utilizar e rastrear vários eventos através do ciclo de vida de um componente. Para uma
lista completa, consulte a [seção "Lifecyle Hooks" na documentação oficial do Angular 2](https://angular.io/docs/ts/latest/guide/lifecycle-hooks.html).

```javascript
// Annotation section
@Component({
  selector: 'street-map',
  template: '<map-window></map-window><map-controls></map-controls>',
})
// Component controller
class StreetMap {
  ngOnInit() {
    // Properties are resolved and things like
    // this.mapWindow and this.mapControls
    // had a chance to resolve from the
    // two child components <map-window> and <map-controls>
  }
  ngOnDestroy() {
    // Speak now or forever hold your peace
  }
  ngDoCheck() {
    // Custom change detection
  }
  ngOnChanges(changes) {
    // Called right after our bindings have been checked but only
    // if one of our bindings has changed.
    //
    // changes is an object of the format:
    // {
    //   'prop': PropertyUpdate
    // }
  }
  ngAfterContentInit() {
    // Component content has been initialized
  }
  ngAfterContentChecked() {
    // Component content has been Checked
  }
  ngAfterViewInit() {
    // Component views are initialized
  }
  ngAfterViewChecked() {
    // Component views have been checked
  }
}
```
