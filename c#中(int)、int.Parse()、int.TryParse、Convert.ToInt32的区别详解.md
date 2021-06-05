## c#中(int)、int.Parse()、int.TryParse、Convert.ToInt32的区别详解

本文对c#中(int)、int.Parse()、int.TryParse、Convert.ToInt32的区别进行了较为深入的详细分析，对初学者而言可以起到巩固学习的目的。详情如下：

**一、(int)变量名[强制类型转换]：**

该转换方式主要用于数字类型转换，从int类型到long,float,double,decimal类型，可以使用隐式转换，但是从long类型到int类型就需要使用显式转换，也就是该数据类型转换方式，否则会产生编译错误。
该方式对于浮点数会做无条件舍去，失去精确度。
当然，该方式也可以进行object到int得转换，但是，object的值要赋予int类型的值，否则会产生编译错误，而且object为null时也会出错。
最后切忌的一点，千万不要用来处理char类型到int类型的转换，否则传回的的值是ASCII代码，而并不是你想要的值。

**二、int.Parse(string类型变量名)**

该方式是将数字内容的字符串转为int类型，如果字符串内容为空或者null时，则抛出ArgumentNullException异常；如果字符串内容不是数字，则抛出FormatException异常；如果字符串内容所表示数字超出int类型可表示的范围，则抛出OverflowException异常。
使用该方法切忌的一点就是**只能处理字符串内容**，而且字符串内容只能在int类型可表示的范围之内。

**三、int.TryParse(string s, out int result)**

该方式也是将数字内容的字符串转为int类型，但是该方式比int.Parse优越的地方，就是它不会出现异常。如果转换成功返回true，如果转换失败返回false。很明显，最后一个参数为输出值，如果转换失败，输出值为0；如果转换成功，则输出相应的值。

**四、Convert.ToInt32**

该方式不仅可以将字符串转为int类型，还可以将其它类型的值转成int类型。变量若为object或string类型，当其值为null时，会传回0，不会造成程序错误，但是若此string类型的值为string.Empty,在转型成int时，仍会造成程序错误。该方式对于浮点数会做四舍五入。
该方式同强制转换一样，不能用来处理char类型，否则传回的是ASCII代码。