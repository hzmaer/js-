# js-execution-context
本文将介绍js执行环境和作用域的概念

1.在局部作用域中定义的变量可以在局部环境中与全局变量互换使用

2.内部环境可以通过作用域链访问所有的外部环境，但是外部环境不能访问内部环境中的任何变量和函数

var color="blue";

    function changeColor(){
    
     var anotherColor="red";

     function swapColors(){
     
      var tempColor=anotherColor;
      
      anotherColor=color;
      
      color=tempColor;
      
      console.debug(anotherColor);
      
     }
     
     swapColors();
     
    }
    
    changeColor();
    
    swapColors可以访问changeColor，changeColor不可以访问swapColors。
    
    3.使用var声明的变量会自动添加到最近的环境中。在函数内部，最接近的环境就是函数的局部环境。在with语句，最接近的环境是函数环境。
    
    function add(num1,num2){
    var sum=num1+num2;
    return sum;
    }
    
    var result=add(10,20);
    alert(sum);//underfined
    4.如果初始化变量时没有使用var声明，该变量会自动被添加到全局环境。
    function add(num1,num2){
    var sum=num1+num2;
    return sum;
    }
    
    var result=add(10,20);
    alert(sum);//30
    
    5.搜索标识符的过程:如果在局部环境中找到了标识符，搜索过程停止，变量就绪。
    
                     如果在局部环境中没有找到该变量名，则继续沿作用域链向上搜索。搜索过程将一直追溯到全局环境的变量对象。如果
                     
                     在全局环境中也没有找到这个标识符，则意味着该变量尚未声明。
                    
