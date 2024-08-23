---
title: ECMAScript
date: 2024-08-19 14:53:00
tags: [ECMAScript]
categories:
- JavaScript
---
## 函数

```javascript
<script>
    //常规函数与箭头函数 [箭头函数是一种匿名函数]
    let plus_normal = function (a, b) {
        return a + b
    }
    let plus_arrow = (a, b) => { //省略 function 添加 =>
        return a + b
    }
    //隐式返回 [在函数体内只有一个表达式的情况下, 可以省略花括号 {} 和 return 关键字]
    let plus2 = (a, b) => a + b
</script>
```

## 数组

```javascript
<script>
    //定义数组
    let arr = [10, 11]

    //向数组末尾添加一个或多个元素, 并返回修改后数组的长度
    let arrLength = arr.push(12, 13) // [10, 11, 12, 13]

    //向数组开头添加一个或多个元素, 并返回修改后数组的长度
    arrLength = arr.unshift(8, 9) // [8, 9, 10, 11, 12, 13]

    //删除数组中第一个元素, 并返回被删除元素
    let delElement = arr.shift() // [9, 10, 11, 12, 13]

    //删除数组最后一个元素, 并返回被删除元素
    delElement = arr.pop() // [9, 10, 11, 12]

    //删除元素, 并返回包含被删除元素的数组 splice(要删除元素的索引位置, 要删除的元素数量)
    let delArr = arr.splice(2, 2) // 删除第3和第4个元素
    console.log("arr", arr) //[9, 10]
    console.log("delArr", delArr) //[11, 12]

    //颠倒数组中元素的顺序
    arr.reverse() // [10, 9]

    //数组中的元素按照首字母顺序排序
    let arr2 = ['banana', 'apple', 'orange']
    arr2.sort()

    //数组中的元素按照数字排序
    let arr3 = [5, 20, 13, 1, 4]
    //arr3.sort() //默认情况下 sort() 方法使用字符串排序, 导致并没有按照数字大小排序
    /*
        比较函数 (a, b) => a - b 接收两个参数 a 和 b, 用于比较这两个元素的大小, 返回 a - b 的结果决定了 sort() 方法的排序顺序
        若 a < b, 则 a - b 是一个负数, 表示 a 应该在 b 前面
        若 a = b, 则 a - b 是 0, 位置保持不变
        若 a > b, 则 a - b 是一个正数, 表示 a 应该在 b 后面
    */
    arr3.sort((a, b) => a - b)
    console.log("arr3", arr3) //[1, 4, 5, 13, 20]

    //筛选符合条件的元素, 返回一个新的数组
    let arr4 = [10, 11, 12, 13, 14, 15]
    let newArr = arr4.filter((value, index) => {
        return value > 12
    })
    console.log("newArr", newArr) //[13, 14, 15]

    //将多个数组或值合并为一个新数组
    let arr5 = ["十六", "十七", "十八"]
    newArr = arr3.concat(arr5) //[1, 4, 5, 13, 20, '十六', '十七', '十八']
    newArr = arr4.concat(arr5, 19, 20) //[10, 11, 12, 13, 14, 15, '十六', '十七', '十八', 19, 20]

    //使用for...of循环遍历数组
    let arr6 = ["哈哈", "google.com", 100] //数组可以包含不同的数据类型

    //使用forEach方法来遍历数组
    arr6.forEach((value,index) => {
        console.log("forEach", value,"index", index)
    })
</script>
```

## 字符串

```javascript
    let web = "google.com"

    // 字符串长度
    let len = web.length

    // 转小写
    let str1 = "DAVID".toLowerCase()

    // 转大写
    let str2 = "luna".toUpperCase()
  
    // 返回字符串在索引处的字符
    let str3 = web[2]

    // 字符串转为字符数组
    let str4 = [...web]

    // 字符串转 int
    let number = parseInt("168")

    // 字符串替换
    let str6 = web.replaceAll("o", "y")
    let str7 = web.replace("o", "y")

    // 去除字符串两侧指定的字符
    let str8 = "   google.com   ".trim()

    // 判断是否包含某个字符串
    let result = web.includes("g") // true

    // 返回字符串中第一次出现某个字符串的位置,若不存在则返回-1
    let result2 = web.indexOf("l") // 4
    let result3 = "www.google.com".indexOf("b") // -1

    // 判断一个字符串是否以指定的前缀开头
    let result4 = "www.google.com".startsWith("www")

    // 判断一个字符串是否以指定的后缀结尾
    let result5 = "www.google.com".endsWith("net")

    // 将字符串按照指定字符分割成数组
    let arr = "a,b,c,d".split(",")

    // 字符串截取 substr(开始位置,截取长度)
    let subStr = web.substr(0, 7) // 从0开始7
    let subStr2 = web.substr(-3) // 最后3
    let subStr3 = web.substr(4) 从0开始4

    //重复字符串
    let repeatstr = "David".repeat(3)

    //在字符串前添加指定数量的填充字符, 直到该字符串达到指定的长度
    let padStart = "David".padStart(15, "-") //由于 David 占 5 个字符, 因此只需要再添加 10 个横线, 即可达到总长度 15
    let padStart = "David".padStart(15) //默认空格
    console.log("padStart:", padStart)

    //在字符串后添加指定数量的填充字符, 直到该字符串达到指定的长度
    let padEnd = "David".padEnd(10, "-")
```

## 解构

```javascript
    //解构 可以从数组或对象中提取值并赋给变量
    //--- 数组解构
    let [x, y] = [1, 2] // x = 1, y = 2

    let [, , c] = [10, 20, 30] // c = 30

    //扩展运算符
    let [A, ...B] = [1, 2, 3, 4, 5, 6]
    console.log("A:", A, "B:", B)

    let [x2, y2 = 200] = [100] //默认值
    console.log("x2:", x2, "y2:", y2)

    //两数交换
    let x3 = 10
    let y3 = 20; //不加分号会报错
    [x3, y3] = [y3, x3]
    console.log("x3:", x3, "y3:", y3)

    //--- 对象解构
    let person = {
        name: '邓瑞',
        gender: '男',
        web: 'dengruicode.com'
    }

    let { name } = person
    console.log("name:", name)

    //重命名
    let { name: userName, gender, web } = person
    console.log("userName:", userName, "gender:", gender, "web:", web)

    //默认值
    let { address = "安徽" } = person
    console.log("address:", address)
```

## Set

```javascript
    //创建Set
    let fruits = new Set()
    let fruits = new Set(['apple', 'orange', 'banana'])

    //添加新的元素
    fruits.add('mango')

    //删除元素
    fruits.delete('banana')

    //检查Set集合是否包含指定元素
    let res = fruits.has('banana')

    //获取Set集合的大小
    let size = fruits.size

    //使用 Array.from() 方法将 Set 转换为 数组
    let arr = Array.from(fruits)

    //使用扩展运算符将 Set 转换为 数组
    let arr2 = [...fruits]

    //扩展运算符是用于展开可迭代对象(如数组、字符串等)
    let web = 'abcd'
    let webArr = [...web] //使用扩展运算符将 字符串 转换为 数组
    console.log("webArr", webArr) //['a', 'b', 'c', 'd']

    //使用for...of循环遍历 Set集合
    for (let item of fruits) {
        console.log("for...of", item)
    }

    //使用forEach方法来遍历 Set集合
    fruits.forEach(value => {
        console.log("forEach", value)
    })

    //清空 Set
    fruits.clear()

    //将 数组 转换为 Set集合 实现数组去重
    let numberArr = [1, 2, 3, 3, 2, 1]
    let numberSet = new Set(numberArr)
```

## Map

```javascript
    //创建Map
    let person = new Map()创建一个空的Map集合
    let person = new Map([
        ["name", "Jeff"],
        ["gender", "男"]
    ])

    //向Map集合中添加新的元素
    person.set('height', 175)

    //删除元素
    person.delete('gender')

    //检查Map集合是否包含指定元素
    let res = person.has('gender')

    //获取Map集合的大小
    let num = person.size

    //将Map集合转换为数组
    let arr = Array.from(person)

    //使用扩展运算符将 Map集合 转换为 数组
    let arr2 = [...person]

    //使用for...of循环遍历Map集合
    //解构可以从数组或对象中提取值并赋给变量
    //[key, value] 就是一种解构语法, 用于将 Map 集合中的键值对解构为 key 和 value 两个变量
    for (let [key, value] of person) {
        console.log("for...of", key, value)
    }

    //使用forEach方法遍历Map集合的键值对
    person.forEach((value, key) => {
        console.log("forEach", key, value)
    })

    //清空Map集合
    person.clear()
```

## 对象

```javascript
    let person = {
        name: "Jeff",
        gender: "男",
        web: "google.com",
    }

    //删除属性
    delete person.gender
    console.log("person", person)

    //检查对象是否包含指定属性
    let has = "gender" in person

    //获取对象的属性数量
    let attrArray = Object.keys(person) 用于获取对象属性名的数组
    let attrNum = Object.keys(person).length

    //将对象转换为数组
    let arr = Object.entries(person) //Object.entries() 用于获取对象的键值对数组

    //使用for...in循环遍历对象 
    //for...of 用于遍历可迭代对象[如数组、Set、Map、字符串等]
    //for...in 用于遍历对象的可枚举属性
    for (let key in person) {
        console.log("for...in", key, person[key])
    }

    //使用forEach方法遍历对象的属性和值
    Object.entries(person).forEach(([key, value]) => {
        console.log("forEach", key, value)
    })

    //清空对象
    person = {}
```

## 类

```javascript
    class Person {
        name  // public
        #web // private

        constructor(name, web) {
            this.name = name
            this.#web = web
        }

        get web() {
            return this.#web
        }

        set web(value) {
            this.#web = value
        }

        info() {
            return `姓名:${this.name} 个人网站:${this.web}`
        }
    }

    let person = new Person("Jeff", "google.com")
```

## Promise

```javascript
        /*
            Promise 表示承诺在未来的某个时刻可能会完成并返回结果

            对于某些需要时间来处理结果的操作, 如用户登录、读取文件等, 可以使用 Promise 对象来执行异步操作
            Promise 对象有三种状态 pending(待处理)、fulfilled(已履行)、rejected(被驳回)

            当创建一个 Promise 对象时, 它的初始状态为 pending, 表示异步执行还未完成
            当异步执行成功时, 会调用 resolve 函数把 Promise 对象的状态改变为 fulfilled, 可通过 then 方法来获取异步操作的结果
            当异步执行异常时, 会调用 reject 函数把 Promise 对象的状态更改为 rejected, 可通过 catch 方法来处理错误

            注
                异步操作是指在程序执行过程中, 某个操作不会立即返回结果, 而是需要一段时间的等待
        */

        /*
            let promise = new Promise((resolve, reject) => {
              
            })

            //当创建一个 Promise 对象时, 它的初始状态为 pending, 表示异步执行还未完成
            console.log("promise:", promise) //pending
        */

        /*
            let promise = new Promise((resolve, reject) => {
                resolve("邮件发送成功") //异步执行成功
            })
            //当异步执行成功时, 会调用 resolve 函数把 Promise 对象的状态改变为 fulfilled, 可通过 then 方法来获取异步操作的结果
            console.log("promise:", promise) //fulfilled

            promise.then(result => {
                console.log("result:", result)
            })
        */

        /*
            let promise = new Promise((resolve, reject) => {
                reject("邮件发送失败") //异步执行失败
            })
            //当异步执行失败时, 会调用 reject 函数把 Promise 对象的状态更改为 rejected, 可通过 catch 方法来处理错误
            console.log("promise:", promise) //rejected

            promise.catch(error => {
                console.log("error:", error)
            })
        */

        let promise = new Promise((resolve, reject) => {
            //resolve("邮件发送成功")
            reject("邮件发送失败")
        }).then(result => {
            console.log("result:", result)
        }).catch(error => {
            console.log("error:", error)
        }).finally(() => {
            console.log("异步执行结束")
        })
```

## Fetch

```javascript
    /*
        fetch 是基于 Promise 的 api, 它可以发送http请求并接收服务器返回的响应数据
        fetch 返回的是一个 Promise 对象
    */

    //get请求
    fetch('http://127.0.0.1/get').then(response => {
        //返回的解析后的json数据会传递给下一个 then() 方法中的回调函数作为参数,这个参数就是 data
        return response.json() //response.json() 用于将响应数据解析为json格式的数据
    }).then(data => { //data 解析后的json数据
        console.log("get.data:", data)
    }).catch(error => {
        console.log("get.error:", error.message)
    }).finally(() => {
        console.log("get.finally")
    })

    //post请求 post
    fetch('http://127.0.0.1/post', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
        },          
        body: new URLSearchParams({//URLSearchParams 用于处理键值对类型的数据,并将其编码为url查询字符串
            name: '邓瑞',
            web: 'dengruicode.com',
        }),
    }).then(response => {
        return response.json()
    }).then(data => {
        console.log("post.data:", data)
    }).catch(error => {
        console.log("post.error:", error.message)
    }).finally(() => {
        console.log("post.finally")
    })

    //post请求 postJson
    fetch('http://127.0.0.1/postJson', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify({//JSON.stringify 用于将对象转换为json字符串
            name: '邓瑞编程',
            web: 'www.dengruicode.com',
        }),
    }).then(response => {
        return response.json()
    }).then(data => {
        console.log("postJson.data:", data)
    }).catch(error => {
        console.log("postJson.error:", error.message)
    }).finally(() => {
        console.log("postJson.finally")
    })
```

## Axios

```javascript
    /*
        Axios 是基于 Promise 的网络请求库, 它可以发送http请求并接收服务器返回的响应数据
        Axios 返回的是一个 Promise 对象

        Axios 不仅可以用于浏览器, 也可以用于 Node.js, 而 Fetch 主要用于浏览器
    */

    //get请求
    axios.get('http://127.0.0.1/get').then(response => {
        console.log("get.data:", response.data)
    }).catch(error => {
        console.log("get.error:", error)
    }).finally(() => {
        console.log("get.finally")
    })

    //post请求 post
    let data = { //参数
        name: '邓瑞',
        web: 'dengruicode.com',
    }

    axios.post('http://127.0.0.1/post', data, {
        headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
        }
    }).then(response => {
        console.log("post.data:", response.data)
    }).catch(error => {
        console.log("post.error:", error)
    }).finally(() => {
        console.log("post.finally")
    })

    //post请求 postJson [axios 的默认请求头是 application/json]
    axios.post('http://127.0.0.1/postJson', data).then(response => {
        console.log("postJson.data:", response.data)
    }).catch(error => {
        console.log("postJson.error:", error)
    }).finally(() => {
        console.log("postJson.finally")
    })
```

## Async & Await

```javascript
async
     当一个函数被标记为 async 后, 该函数会返回一个 Promise 对象

await
     只能在 async 函数内部使用, 加上 await 关键字后, 会在执行到这一行时暂停函数的剩余部分，

     等待网络请求完成,然后继续执行并获取到请求返回的数据



<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="axios/dist/axios.min.js"></script>
</head>

<body>
  <script>

    //回调地狱是指过度使用嵌套的回调函数,导致代码难以阅读和维护
    //get请求
    axios.get('http://127.0.0.1/get').then(response => {
      console.log("get.data:", response.data)
      if (response.data.data.web == "dengruicode.com") {

        //get请求2
        return axios.get('http://127.0.0.1/article/get/id/1').then(response2 => {
          console.log("get2.data:", response2.data)
          if (response2.data.data.name == "邓瑞") {

            //get请求3
            return axios.get('http://127.0.0.1/article/get/search/title/入门').then(response3 => {
              console.log("get3.data:", response3.data)
            })
          }
        })
      }
    }).catch(error => {
      console.log("get.error:", error)
    }).finally(() => {
      console.log("get.finally")
    })

    //async/await 使用同步的方式编写异步代码, 避免回调地狱
    //优势 在处理多个异步操作的情况下, 可以使代码更简洁易读
    const getData = async () => {
      try {
        //get请求
        const response = await axios.get('http://127.0.0.1/get')
        console.log("async.get.data:", response.data)
        if (response.data.data.web === "dengruicode.com") {

          //get请求2
          const response2 = await axios.get('http://127.0.0.1/article/get/id/1')
          console.log("async.get2.data:", response2.data)
          if (response2.data.data.name === "邓瑞") {

            //get请求3
            const response3 = await axios.get('http://127.0.0.1/article/get/search/title/入门')
            console.log("async.get3.data:", response3.data)
          }
        }

      } catch (error) {
        console.log("async.get.error:", error)
      } finally {
        console.log("async.get.finally")
      }
    }

    getData()

  </script>
</body>

</html>

```
