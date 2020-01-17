# Js best practics
List of favorite moments

- [List](#root)
  - [Composition](#composition)
  - [Proxy (get)](#proxy-get)

### Composition
```javascript
const f1 = (arg) => (console.log('f1', arg), arg + 1)
const f2 = (arg) => (console.log('f2', arg), arg + 1)
const f3 = () => (console.log('f3'), 1)

const funcs = [f1, f2, f3]
const arg = 0

const g = funcs.reduce((a, b) => (arg) => a(b(arg)))

const f = funcs.reduce(function(a, b) {
  return function(arg) {
    return a(b(arg))
  }
})

// f === g

console.log(f())
//        output
// f3
// f2 1
// f1 2
// 3
```
### Proxy get
```javascript
const person = {
  name: 'Jack Sparrow',
  job: 'Pirate',
  role: 'captain',
}

const op = new Proxy(person, {
  get(target, prop) {
    if (!(prop in target)) {
      return prop
        .split('_')
        .map((p) => target[p])
        .join(' ')
    }
    return target[prop]
  },
})
```
