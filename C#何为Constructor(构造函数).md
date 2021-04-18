## 何为Constructor(构造函数)

**Constructor 构造函数，基本用法是在类对象声明的时候完成初始化工作**

```c++
    class Chinar
    {
        private int    a = 1;
        private int    b = 1;
        private string c = "Chinar";
        private object d = 666;


        //构造函数用来完成 —— 初始化工作
        public Chinar() //声明一个名称与类名一样的函数，就是构造函数（可以传你所需要的参数，写你所需的方法） 
        {
            //每个类，本身默认有一个。如果我们不写明这个  public Chinar()函数，系统仅调用系统默认的。
            //自定义构造 public Chinar()函数后，系统只会调用自定义的 Chinar（）
        }


        //这是一个多参数的构造函数
        public Chinar(int a, int b, string c, object d)
        {
        }
        
        
    }
```



#### C#中静态构造函数:

使用静态构造函数的一个原因是：在第一次使用类之前，用静态构造函数来初始化类(当然也包括结构体，这里用类做阐述)中一些静态字段或属性。比如对字段或属性进行一系列的操作进行初始化，而不希望每次实例化类的时候改变他，用静态构造函数比较方便。

```c++
public class MyClass
{
	static MyClass()
	{
 
	}
}
```

注意：静态构造函数没有访问修饰符，不能带任何参数，一个类只能有一个静态构造函数，只能访问类的静态成员(常量也是静态成员)他只是在第一次加载类的时候被调用。