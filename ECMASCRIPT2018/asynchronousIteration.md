#异步迭代  
本章分享由Domenic Denicola 和 Kevin Smith提出的ECMAScript目标  
##异步迭代  
在ECMAScript6中，javascript内置了对于对同步迭代数据的支持。但是，对于文本文件、异步读取文件、http链接等异步行为并没有很好的支持。  
现在我们想要实现对此类数据的支持，在我们开始之前，我们首先回归一下同步迭代。
##同步迭代
同步迭代在ES6被引入，运行流程如下：  
- 迭代性（Iterable）：一个对象是否是一个可以通过键值为`Symbol.iterator`进行迭代  
- 迭代器（Iterator）：通过在iterable上调用[Symbol.iterator]（）返回的对象。 它将每个迭代元素包装在一个对象中，并通过其next（）方法一次一个的返回它。  
- 迭代结果（IteratorResult）：next（）方法返回的对象。其中有两个属性：属性Value包含一个迭代器；属性done在最后一个迭代元素完成后为ture。（value通常都可以被忽略了，因为其经常是undifined）。
我们通过一个例子来说明一下：  
> const iterable = ['a', 'b'];
> const 