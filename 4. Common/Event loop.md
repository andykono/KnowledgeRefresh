
Порядок выполнения команд в Event Loop 
- Не синхронные команды. 
- Micro Tasks как-то Promise.resolve().then() 
- Macro Tasks, как setTimeout, Клики, скролл *(это Web API)*

```js
console.log(1);

setTimeout(function() {
  console.log(2);
});

Promise.resolve(3).then(console.log);

console.log(4);

setTimeout(function() {
  console.log(5);
}, 0);

console.log(6);

/*
Напишите порядок вывода чисел:
1 4 6 3 2 5
*/
```


```javascript
console.log(1);

setTimeout(function() {
  console.log(2);
});

Promise.resolve(3).then(console.log);

console.log(4);

setTimeout(function() {
  console.log(5);
}, 0);

console.log(6);

const foo2 = () => {
	console.log("foo2");
	
	settimeout(foo2);
}

/*
Напишите порядок вывода чисел:
1 4 6 foo2 3 2 5 foo2
*/
```