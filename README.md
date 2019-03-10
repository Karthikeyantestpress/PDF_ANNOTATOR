# pdf-annotate.js

[![build 
status](https://img.shields.io/travis/com/Submitty/pdf-annotate.js.svg?style=flat-square)](https://travis-ci.com/Submitty/pdf-annotate.js)

Annotation layer for [pdf.js](https://github.com/mozilla/pdf.js). Fork of [instructure/pdf-annotate.js](https://github.com/instructure/pdf-annotate.js/) and DynamicEnvironmentSystems/pdf-annotate.js, developed for usage within Submitty.

## Objectives

- Provide a low level annotation layer for [pdf.js](https://github.com/mozilla/pdf.js).
- Optional high level UI for managing annotations.
- Agnostic of backend, just supply your own `StoreAdapter` to fetch/store data.
- Prescribe annotation format.

## Example

```js
import pdfjsLib from 'pdfjs-dist/build/pdf';
import PDFJSAnnotate from 'pdfjs-annotate';
import MyStoreAdapter from './myStoreAdapter';

const { UI } = PDFJSAnnotate;
const VIEWER = document.getElementById('viewer');
const RENDER_OPTIONS = {
  documentId: 'MyPDF.pdf',
  pdfDocument: null,
  scale: 1,
  rotate: 0
};

pdfjsLib.workerSrc = 'pdf.worker.js';
PDFJSAnnotate.setStoreAdapter(MyStoreAdapter);

pdfjsLib.getDocument(RENDER_OPTIONS.documentId).then((pdf) => {
  RENDER_OPTIONS.pdfDocument = pdf;
  VIEWER.appendChild(UI.createPage(1));
  UI.renderPage(1, RENDER_OPTIONS);
});
```

See more [examples](https://github.com/Submitty/pdf-annotate.js/tree/master/examples).

## Documentation

[View the docs](https://github.com/Submitty/pdf-annotate.js/tree/master/docs).

## Developing

```bash
# clone the repo
$ git clone https://github.com/Submitty/pdf-annotate.js.git
$ cd pdf-annotate.js

# intall dependencies
$ npm install

# start example server
$ npm start
$ open http://127.0.0.1:8080

# run tests
$ npm test
```

