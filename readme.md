#算法
##线性结构

###排序

原生方法
>Array.sort 不传入比较函数会先转字符串再根据Unicode比较大小
    
1. 冒泡
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
    
2. 快排
    
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
###去重

###翻转

##树形结构

##网状结构

#网络
##七层结构
##三次握手
##HTTP
##POST\GET
##状态码
##请求头
##响应头

#HTML  BOM  DOM
#JavaScript
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
    
##事件循环
    
##ES6
- var let const
- map set
- 箭头函数

    1. 默认参数
    2. this 指向定义的上下文
    3. 不能new
    4. 没有arguments
    5. 不能Generator

- Promise
- generator yield
- async await 
- class
- module

##AMD/CMD

##函数式编程
#CSS
- BFC
- flex布局
#网络安全
##XSS
##CSRF
#性能
##浏览器工作流程
##缓存
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
##浏览器渲染
##移动端
#框架
##Vue
###生命周期
   new Vue() -> Init(Event Lifecycle) -> beforeCreate -> Init(injections reactivity) -> get Render Function -> beforeMount -> mounted -> beforeUpdate -> re-render -> update -> beforeDestroy -> destroy -> destroyed
###双向绑定
###依赖收集
###watcher

#新技术
#架构设计
#个人成长
