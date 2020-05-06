### java8实战
前10章代码实战

每一章的包中有一个Main.java文件，里面说明了本章节的主要内容，
chapter1表示第一章，chapter4_5表示第四章和第五章。

####待解决问题
>* 1、使用flatMap重构链式编程，chapter10中Main方法未注释的代码部分会抛出空指针异常?

####answer:
> * 1 这个问题很简单，报错的不是System.out.println(name)这一行，而是这一行 .flatMap(Person::getCar)
      你进入flatMap方法的的源码就会发现有这么一行代码 Objects.requireNonNull(mapper.apply(value)) 这句话执行mapper.apply(value),就会
      真正的调用你的person.getCar方法，你打个断点就知道调用顺序了，lambda其实就是只有一个参数的匿名内部类而已，但是你的这个person.getCar返回为null
      Objects.requireNonNull参数为null就报空指针异常了，你跟进去源码看就明白了
      
> * 2 另外flatMap的使用场景也是错误的，一般的flatMap用于嵌套对象的拆解，或者多维度数组转换为单一数组，单个的对象一般使用map。
      遇到问题，先跟踪源码，看哪里报错，尝试解决；还要有正确的学习方式，学习新东西，层层递进学习，不要急，先把要学习的东西最基础的概念
      搞清楚，再使用