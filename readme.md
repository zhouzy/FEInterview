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
