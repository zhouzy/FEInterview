该系列分两个部分。
第一部分是前端工程中，所使用的基本工具包括算法、JS、CSS、HTML、网络、工具、模式等等
的目的是为了，加深对前端工具箱中工具的熟练度；
第二部分，主要是记录目前产品、项目中遇到的问题，然后我是怎么分析问题，然后怎么去解决的

第一部分对于每一个点，说清楚是什么、怎么用、出现的原因、出现这个技术主要解决什么问题。

# 算法
## 线性结构
### 排序

原生方法
>Array.sort 不传入比较函数会先转字符串再根据Unicode比较大小
    
1. 插入排序
2. 选择排序
3. 冒泡排序
    ```javascript 1.5
    function sort(list){
        if(!list || !Array.isArray(list)){
            return;
        }
        for(var i=0,l=list.length-1; i<l; i++){
            /*for(var j=0, len=list.length-1; j<len; j++){
                if(list[j] > list[j+1]){
                    var t = list[j]; list[j] = list[j+1]; list[j+1] = t;
                }
            }*/
            //优化
            for(var j=0, len=list.length-1-i; j<len; j++){
                if(list[j] > list[j+1]){
                    var t = list[j]; list[j] = list[j+1]; list[j+1] = t;
                }
            }
        }
    }
    ```
4. 快速排序
    
    ```javascript 1.5
    function quickSort(list){
        function _qs(list,l,r){
            if(l >= r){
                return;
            }
            var _l = l;
            var _r = r;
            var temp = list[l];

            while(l < r){
                while(list[r] > temp && l < r){
                    r--;
                }
                while(list[l] < temp && l < r){
                    l++;
                }
                if(l < r){
                    /*找到右侧比基数小左侧比基数大的两个数，交换位置*/
                    var t = list[r]; list[r] = list[l]; list[l] = t;
                }
            }
            console.log(list);
            _qs(list,_l,l-1);
            _qs(list,l+1,_r);
        }

        if(!list || !Array.isArray(list)){
            return;
        }
        _qs(list, 0, list.length - 1);
    }
    ```

5.堆排序    
    
6. 1000个 1-10000 的数，求其中质数

```javascript 1.6
    let isPrime = (num) => {
        let s = "" + num; 
        let t = 0;
        
        if(num <= 1){
            return false;
        }
        if(s.endsWith("5") || s.endsWith("2")){
            return false;
        }
        s.split("").forEach(n => {
            t += (+n);
        });
        if(t % 3 === 0){
            return false;
        }
        for(let i = 2; i < (num - 1); i++){
            if(num % i === 0){
                return false;
            }
        }
        return true;
    }
```

### 去重

### 翻转

## 树形结构

## 网状结构

# 网络
## 七层结构
## 三次握手
## HTTP
## POST\GET
## 状态码
## 请求头
## 响应头
## 网络安全
### XSS
### CSRF
# HTML  BOM  DOM
# JavaScript
## 隐式转换
## 变量提升
## 继承实现方式
- 类式继承
    ```javascript 1.5
    function P(){}
    function C(){}
    C.prototype = new P();
    ```
    缺陷:
    
- 构造函数继承
    ```javascript 1.5
    function P(){}
    function C(){
        P.apply(this,arguments);
    }
    ```
    缺陷:
    
- 组合继承
    ```javascript 1.5
    function P(){}
    function C(){
        P.apply(this,arguments);
    }
    C.prototype = new P();
    ```
    缺陷：P的构造函数被调用了两次
    
- 寄生组合式继承
    ```javascript 1.5
    function P(){}
    function C(){
        P.apply(this,arguments);
    }
    C.prototype = object.create(P.prototype);
    C.prototype.constructor = C;  
    ```
    
## 事件循环
    
## ES6
- let const
    - let: 
    
    let 用于声明变量，它有以下几个特性；
    1. 只在作用域中有效
    ```javascript 1.6
    {
      let a = "1"; 
      var b = "1"; 
    }
    console.log(b);//1
    console.log(a);//error
    ```
    
    2. 不会变量提升
    let 声明变量，不会变量提升
    ```javascript 1.6
    var a = 234;
    {
      console.log(b);//undefined
      console.log(a);//error
      let a = 123;
      var b = 2;
    }
    ```
    3. 对var定义的变量封锁
    ```javascript 1.6
    var a = 1;
    {
      let a = 2;  
      console.log(a);
    }

    ```
- Map Set

- 箭头函数

    1. 默认参数
    2. this 指向定义的上下文
    3. 不能new
    4. 没有arguments
    5. 不能Generator

- Promise

    Promise是操作异步处理对象的组件

    1. new Promise()
    
    ```javascript 1.6
    /**
     * 传入的function 会立即执行
     */
    let p = new Promise((resolve, reject) => {
      console.log("1");  
      resolve(3);
    });
  
    console.log("2");
  
    p.then((d) => {
      console.log(d);
    });
  
    //打印 1 2 3
    ```
    2. then
    ```javascript 1.6
    //then 返回的是一个新的promise
    let p = new Promise(() => {
      console.log("promise init");
    });
    let p2 = p.then(() => {
      console.log("promise then");
    });
    console.log(p === p2);
  
    //异常处理
    new Promise((resolve, reject) => {
      console.log("promise init");
      throw new Error("some error");
      reject("reject error");
    })
    .then(() => {
      console.log("promise then");
    }, (err) => {
      console.log("p2 catch error: %s", JSON.stringify(err));
    })
    .then((data) => {
      console.log("p3 resolve: %s", JSON.stringify(data));  
    }, (err) => {
      console.log("p3 catch error: %s", JSON.stringify(err));  
    })
    .catch(err => {
      console.log("fainlly catch error: %s", JSON.stringify(err));  
    });
  
    // p2 reject 会被调用
    // p3 resolve 会被调用
    // catch 不会调用
    ``` 
    3. resolve
    
    4. reject
      
- generator yield

- async await 
- class
- module

## AMD/CMD

## 函数式编程
# CSS
- Flex

    [阮一峰老师讲得很清楚了](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
    
    使用 Flex 实现瀑布流布局

- BFC

- Flip 效果


# 性能
## 浏览器工作流程
## 缓存
- 静态资源
    1. Expires
    2. Cache-Control
        >max-age （s）指定设置缓存最大的有效时间，当浏览器向服务器发送请求后，在max-age这段时间里浏览器直接取本地缓存
        
        >s-maxage (s) 只用于共享缓存，覆盖max-age
        
        >public 共享资源
        
        >private 私有资源
        
        >no-cache 先询问服务器是否有更新，304用本地
        
        >no-store 不缓存
    3. Last-modified 最后修改时间，请求时会带上，服务器用于判断是否返回304
    4. ETag 根据文件内容产生的hash
    
    强制缓存，通过文件hash的方式来更新
- storage
    1. LocalStorage 与 SessionStorage的区别
    2. storage 大小限制
    3. 常用方法
    4. 事件监听
## 浏览器渲染
## 移动端
# 框架
## Vue
### 生命周期
   new Vue() -> Init(Event Lifecycle) -> beforeCreate -> Init(injections reactivity) -> get Render Function -> beforeMount -> mounted -> beforeUpdate -> re-render -> update -> beforeDestroy -> destroy -> destroyed
### 双向绑定
### 依赖收集
### Watcher

# 新技术
# 架构设计
