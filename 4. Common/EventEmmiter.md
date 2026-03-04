Необходимо реализовать класс **EventEmitter** с возможностью подписки на разные события, отписки и оповещения о событии для всех подписчиков. 

```js
class EventEmitter {
    // Реализуйте класс
    constructor() {
        this.events = {};
    }

    on(event, callback) {
        if (!this.events[event]) {
            this.events[event] = [];
        }
        this.events[event].push(callback);

        return this;
    }

    off(event, callback) {
        if (!this.events[event]) return this;
        this.events[event] = this.events[event].filter(cb => cb !== callback);
        return this;
    }

    emit(event, ...args) {
        if (!this.events[event]) return this;
        this.events[event].forEach(cb => cb(...args));
        return this;
    }
}
```

 но лучше реализовать через **Set** хранилище событий, чтобы не было дубликатов.