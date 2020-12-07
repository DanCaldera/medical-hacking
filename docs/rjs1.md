---
id: rjs1
title: El Javascript que debes conocer para programar con React
sidebar_label: Javascript elemental
---

## Template Literals

#### o Plantillas de Texto

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

## Arrow Functions

#### o Funciones Flecha

Es solo otra manera de escribir funciones, un poco más resumida y de forma más implícita.

```javascript {16,17,18,19,20}
const returnFive = () => 5
const multiply = (a, b) => a * b

// Es lo mismo que:
function returnFive() {
  return 5
}
function multiply(a, b) {
  return a * b
}

// En React:
function ShowList({ elements }) {
  return (
    <ul>
      {elements.map((elem) => (
        <li key={elem.id}>
          <span>{elem.name}</span>
        </li>
      ))}
    </ul>
  )
}
```

## Shorthand property names

#### o Nombre de Propiedades Abreviadas

```js {11}
const a = 'hola'
const b = 30
const c = { d: [true, false] }
console.log({ a, b, c })

// Es lo mismo que::
console.log({ a: a, b: b, c: c })

// en React:
function Counter({ initialCount, step }) {
  const [count, setCount] = useCounter({ initialCount, step })
  return <button onClick={setCount}>{count}</button>
}
```

## Destructuring

#### Desestructuración

```js
const obj = { x: 3.6, y: 7.8 }
makeCalculation(obj)

function makeCalculation({ x, y: d, z = 4 }) {
  return Math.floor((x + d + z) / 3)
}

// es lo mismo que:
function makeCalculation(obj) {
  const { x, y: d, z = 4 } = obj
  return Math.floor((x + d + z) / 3)
}

// que a su vez es igual que:
function makeCalculation(obj) {
  const x = obj.x
  const d = obj.y
  const z = obj.z === undefined ? 4 : obj.z
  return Math.floor((x + d + z) / 3)
}

// en React:
function UserGitHubImg({ username = 'ghost', ...props }) {
  return <img src={`https://github.com/${username}.png`} {...props} />
}
```

```js
function nestedArrayAndObject() {
  // refactorizando esto an una sola línea...
  const info = {
    title: 'Once Upon a Time',
    protagonist: {
      name: 'Emma Swan',
      enemies: [
        { name: 'Regina Mills', title: 'Evil Queen' },
        { name: 'Cora Mills', title: 'Queen of Hearts' },
        { name: 'Peter Pan', title: `The boy who wouldn't grow up` },
        { name: 'Zelena', title: 'The Wicked Witch' },
      ],
    },
  }
  // const {
  //   title,
  //   protagonist: { name, enemies },
  // } = info // <-- queda así, aunque aún se puede desestructurar más

  // otra manera
  const title = info.title
  const protagonistName = info.protagonist.name
  const enemy = info.protagonist.enemies[3]
  const enemyTitle = enemy.title
  const enemyName = enemy.name
  return `${enemyName} (${enemyTitle}) is an enemy to ${protagonistName} in "${title}"`
}
```
