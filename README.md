# Js best practics
List of favorite moments

- [List](#root)
  - [Composition](#composition)

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
