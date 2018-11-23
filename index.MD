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
    
    ``` javascript 1.5
        function quickSort(list){
            if(!list || !Array.isArray(list)){
                return;
            }   
            for(var i=0,l=list.length-1; i<l; i++){
                for(var j=0, len=list.length-1-i; j<len; j++){
                    if(list[j] > list[j+1]){
                        var t = list[j]; list[j] = list[j+1]; list[j+1] = t;
                    }
                }
            }   
        }
    ```
###去重
###翻转

##树形结构
##网状结构
#网络
#HTML  BOM  DOM
#JavaScript
##ES6
##Promise
##AMD
##CMD
##函数式编程
#CSS
#框架
#新技术
#架构设计
#个人成长
