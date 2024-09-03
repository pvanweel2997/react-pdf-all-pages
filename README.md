# react-pdf-all-pages-js

`react-pdf-all-pages-js` provides a component for rendering PDF documents using [PDF.js](http://mozilla.github.io/pdf.js/).

---

[![NPM Version](https://img.shields.io/npm/v/@pvanweel2997/react-pdf-all-pages.svg?style=flat-square)](https://www.npmjs.com/package/@pvanweel2997/react-pdf-all-pages)
[![NPM Downloads](https://img.shields.io/npm/dm/@pvanweel2997/react-pdf-all-pages.svg?style=flat-square)](https://www.npmjs.com/package/@pvanweel2997/react-pdf-all-pages)
[![codecov](https://codecov.io/gh/pvanweel2997/react-pdf-all-pages-js/branch/master/graph/badge.svg)](https://codecov.io/gh/pvanweel2997/react-pdf-all-pages-js)

# Usage

Install with `yarn add @pvanweel2997/react-pdf-all-pages pdfjs-dist` or
`npm install @pvanweel2997/react-pdf-all-pages pdfjs-dist`

## `usePdf` hook

Use the hook in your app (comes with built-in 3d page look out of the box):

```js



const PDFFileViewer2 = ({ file }: { file: DocFile }) => {
  const { pdfDocument } = usePdf({
    file: file.url,
    pdfLocation: "pdfdoc",
  });

  return (
     <div>
      {!pdfDocument && <span>Loading...</span>}
      <div id="pdfdoc"/>
    </div>
  );
};



```

## Props

When you call usePdf you'll want to pass in a subset of these props, like this:

> `const { pdfDocument,} = usePdf({ pdfLocation, file: 'https://example.com/test.pdf', page });`

### pdfLocation

an id of an element where you want your pages to display.

### file

URL of the PDF file.

### onDocumentLoadSuccess

Allows you to specify a callback that is called when the PDF document data will be fully loaded.
Callback is called with [PDFDocumentProxy](https://github.com/mozilla/pdf.js/blob/master/src/display/api.js#L579)
as an only argument.

### onDocumentLoadFail

Allows you to specify a callback that is called after an error occurred during PDF document data loading.

### onInvalidLocation

Allows you to specify a callback that is called if the pdfLocation html element is not found.

### scale

Allows you to scale the PDF. Default = 1.

### rotate

Allows you to rotate the PDF. Number is in degrees. Default = 0.

### cMapUrl

Allows you to specify a cmap url. Default = '../node_modules/pdfjs-dist/cmaps/'.

### cMapPacked

Allows you to specify whether the cmaps are packed or not. Default = false.

### workerSrc

Allows you to specify a custom pdf worker url. Default = '//cdnjs.cloudflare.com/ajax/libs/pdf.js/\${pdfjs.version}/pdf.worker.js'.

### withCredentials

Allows you to add the withCredentials flag. Default = false.

### className

Allows you to style your pdf pages by passing in a className.

### useDefaultStyle (defaults to true)

Specified whether to use the built-in styling or not to use the built-in styling.

## Returned values

### pdfDocument

`pdfjs`'s `PDFDocumentProxy` [object](https://github.com/mozilla/pdf.js/blob/master/src/display/api.js#L579).
This can be undefined if document has not been loaded yet.

# License

MIT © [pvanweel2997](https://github.com/pvanweel2997)
