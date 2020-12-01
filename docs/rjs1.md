---
id: rjs1
title: El Javascript que debes conocer para programar con React
sidebar_label: Javascript Básico
---

## Template Literals

```javascript
const str1 = 'Hello'
const str2 = 'World'
console.log(`${str1} ${str2}!`) // Hello World!

// es lo mismo que:
console.log(str1 + ' ' + str2 + '!')

// en React sería:
function ProgressBar({ className, ...props }) {
  return <div className={`progressBar ${className}`} {...props} />
}
```
