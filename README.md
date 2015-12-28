# Angular2 translate

This is a simple translate service solution for angular2. You should provide a dictionary and the service will translate it with sprintf interpolation.

Install
---------

```bash
npm install --save angular2-translate
```
Setup
---------

```javascript

import { TranslateService } from 'angular2-translate';

const translations = {
  main: {
    text: 'I am: %s you are: %s'
  },
  other: {
    withoutInterpolation: 'Star Wars'
  }
};

@Component({
  selector: '<app>',
  template: `
    Your main app
  `
})
export class App {

  constructor(translateService: TranslateService) {
    translateService.setTranslations(translations);
  }
```

Usage in template
---------

```javascript

import { TranslatePipe } from 'angular2-translate';

@Component({
  selector: '<sub-app>',
  pipes: [TranslatePipe],
  template: `
    <h1>{{ 'main.text' | translate:'Luke':controllerVariable }}</h1>
    <h2>{{ 'other.withoutInterpolation' | translate }}</h2>
  `
})
export class App {

  constructor() {
    this.controllerVariable = 'Darth Vader';
  }
```

Usage in Controller
---------

```javascript

import { TranslateService } from 'angular2-translate';

@Component({
  selector: '<sub-app>',
  template: `Some content`
})
export class App {

  constructor(translateService: TranslateService) {
    this.translated = translateService.translate('main.text', ['first', 'second']);
  }
```
