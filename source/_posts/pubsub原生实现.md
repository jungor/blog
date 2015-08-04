title: pubsub原生实现
date: 2015-08-04 01:48:35
tags: javascript
---
PubSub 模式的实现如此简单，以至于用十几行代码就能建立自己的
PubSub 实现。对于支持的每种事件类型，唯一需要存储的状态值就
是一个事件处理器清单。

```javascript
var PubSub = {handlers: {}}
```

需要添加事件监听器时，只要将监听器推入数组末尾即可（这意味着
总是会按照添加监听器的次序来调用监听器） 。

```javascript
PubSub.on = function(eventType, handler) {
    if (!(eventType in this.handlers)) {
        this.handlers[eventType] = [];
    }
    this.handlers[eventType].push(handler);
    return this;
}
```

接着，等到触发事件的时候，再循环遍历所有的事件处理器。

```javascript
PubSub.emit = function(eventType) {
    var handlerArgs = Array.prototype.slice.call(arguments, 1);
    for (var i = 0; i < this.handlers[eventType].length; i++) {
        this.handlers[eventType][i].apply(this, handlerArgs);
    }
    return this;
}
```

**PS：这里只实现了注册事件功能，没有删除事件等功能**
