# js-execution-context
本文将介绍js执行环境和作用域的概念

在局部作用域中定义的变量可以在局部环境中与全局变量互换使用

内部环境可以通过作用域链访问所有的外部环境，但是外部环境不能访问内部环境中的任何变量和函数

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
