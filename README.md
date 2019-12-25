# js-queue

#### 项目介绍

- js-queue


#### 使用
- 为测试明了将各demo拷贝单独执行
##### 
```javascript

  // *** 001

  var queue = new Queue();

  queue.push2queue(function (next, again) {
    console.log('a1');

    setTimeout(function () {
      next();
    }, 1000);
  });

  queue.push2queue(function (next, again) {
    console.log('a2');
    setTimeout(function () {
      queue.next();
    }, 1000);
  });

  queue.push2queue(function (next, again) {
    console.log('a3');
    queue.next();
  });


  // *** 002

  var queue2 = new Queue();

  queue2.push2queue(function (next, again) {

    setTimeout(function () {
      if (Math.random() > 0.5) {
        console.log('again');
        again();
      } else {
        console.log('next');
        next();
      }
    }, 1000);
  });


  // *** 003


  var queue3 = new Queue();

  queue3.push2queue(function (next, again) {
    console.log('b1');
    next();
  });

  queue3.push2queue(function (next, again) {
    console.log('b2');
    setTimeout(function () {
      queue3.prev();
    }, 1000);
  });

  // *** 004

  var queue4 = new Queue();

  queue4.push2queue(function (next, again) {
    console.log('c1');
    next();
  });

  queue4.push2queue(function (next, again) {
    queue.next();
    console.log('c2');

  });
  queue4.push2queue(function (next, again) {
    console.log('c3');
    next();
  });


  // *** 005

  var queue5 = new Queue();

  for (var i = 0; i < 10; i++) {
    queue5.push2queue(function (next) {
      console.log('d-index' + queue5.getIndex());
      next();
    });
  }
  console.log('d-queueList' + queue5.getQueue());


  // *** 006

  var queue6 = new Queue();
  queue6.push2queue(function (next, again) {
    console.log(next === queue6.next); // true
    console.log(again === queue6.again); // true

  });


  // *** 007
  // 实例方法已经实现了所有Array.prototype上的方法

  var queue7 = new Queue();

  queue7.push2queue(function (next) {
    next();
  });

  function test() {
  }

  queue7.push(test);
  console.log(queue7.getQueue()[1] === test); // true
  console.log(queue7.pop() === test); // true
  console.log(Object.keys(queue7)); //["concat", "find", "findIndex", "pop", "push", "shift", "unshift", "slice", "splice", "includes", "indexOf", "keys", "entries", "forEach", "filter", "map", "every", "some", "reduce", "reduceRight", "toString", "toLocaleString", "join", "reverse", "sort", "lastIndexOf", "copyWithin", "fill", "values", "flat", "flatMap", "push2queue", "prev", "next", "again", "getIndex", "getQueue", "empty"]

  // *** 008
  // apis
  // queue.push2queue(fn) // 添加队列并立即执行
  // queue.again()  // 重新执行当前对应的队列
  // queue.prev()  // 执行上一个
  // queue.next()  // 执行下一个
  // queue.getIndex() // 获取当前队列位置
  // queue.getQueue() // 获取队列列表
  // queue.empty() // 清空队列


  //
  //
  //
  //
  //
  //

```
