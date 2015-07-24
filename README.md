数组常见操作包含了 增、删、查、改、插入、交集、并集，现整理如下：


1、数组整体元素修改
        //map,给数组每个元素加1 输出[1,2,3]
        $.map([0,1,2],function(n){
            return n+1;
        })


2、 数组筛选
        $.map([0,1,2],function(n){
            return n>0?n+1:null
        })
        //[2,3]


3、jquery 元素转数组
        $("li").toArray()
        $.makeArray($("li"))


4、获取两个数组中相同部分或者不同部分
        //去掉true则显示相同部分，保留true则显示不同部分
        var a=[1,2,3,5,6,3,7,12],
             b=[1,3,5,12]

        $.grep(a,function(n,i){
             if(b.indexOf(n)>=0)
                 return n
        },true);
        //[2, 6, 7]

5、数组去重并倒序排序
        var a=[1,2,3,5,6,3,7,12];
        $.unique(a)
        //[12, 7, 6, 5, 3, 2, 1]


6、数组排序
        var arr=[1,34,5,8,4,9,12]
        arr.sort(function(a,b){
            return a-b;
        });
        //顺序：a-b   [1, 4, 5, 8, 9, 12, 34]
        //倒序：b-a   [34, 12, 9, 8, 5, 4, 1]

7、数组截取slice
        var arr=[1,34,5,8,4,9,12];
            arr.slice(2,4) // [5, 8]
        //arr  输出 [1, 34, 5, 8, 4, 9, 12]


7、数组插入、删除splice(需明确位置)
        var arr=[1,34,5,8,4,9,12];
        //删除
             arr.splice(2,4)
            //arr  输出[1, 34, 12]
        //替换
            arr.splice(1,2,3,4)
            //arr  输出[1, 3, 4, 8, 4, 9, 12]
        //插入
            arr.splice(2,0,44)
        //arr  输出[1, 34, 44, 5, 8, 4, 9, 12]


8、数组遍历
        var members=["1","2","3"];
        $.each(members,function(i,item){
            console.log(item);
        });
        //如何跳出当前的each循环
        //return false;——跳出所有循环；相当于 javascript 中的 break 效果。
        //return true;——跳出当前循环，进入下一个循环；相当于 javascript 中的 continue 效果。


9、jQuery根据元素值删除数组元素的方法
        var arr = ['a','b','c','d'];
        arr.splice($.inArray('c',arr),1);
        console.log(arr);
        //["a", "b", "d"]


10、常见的数组操作

push、pop、shift、unshift


11、数组操作兼容性

    IE8下
    $.inArray 代替 indexOf

    $.grep代替Array.prototype.filter



12、常见数组操作案例：


1、jquery实现从数组移除指定的值

    function delItem(arr,m)
    {
        return $.grep(arr,function(n,i){
            return n!=m
        });
    }
    var a=[1,2,3,5,6,3,7,12];
    delItem(a,3)

或者

    function delItem(arr,m)
    {
        arr.splice($.inArray(m,arr),1);
        return arr
    }
    var arr = ['a','b','c','d'];
    delItem(arr,"c")


2、jquery实现从数组移除指定的数组

    function delArray(arr,delArr)
    {
        return $.grep(arr,function(n,i){
            if( delArr.indexOf(n)>=0)
            return n
        },true);
    }
    var a=[1,2,3,5,6,3,7,12],
         b=[5,7];
    delArray(a,b)


3、jquery找出2个数组同有的部分

    function findCommonArray(arr,delArr)
    {
        return $.grep(arr,function(n,i){
            if( delArr.indexOf(n)>=0)
                return n
        });
    }
    var a=[1,2,3,5,6,3,7,12],
         b=[5,7,9];
    findCommonArray(a,b)
