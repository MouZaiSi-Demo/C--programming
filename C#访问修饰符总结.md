## C#访问修饰符总结

- C#共有五种访问修饰符：public、private、protected、internal、protected internal。作用范围如下表：

|     访问修饰符     | 说明                                                 |
| :----------------: | :--------------------------------------------------- |
|       public       | 公有访问。不受任何限制。                             |
|      private       | 私有访问。只限于本类成员访问，子类，实例都不能访问。 |
|     protected      | 保护访问。只限于本类和子类访问，实例不能访问。       |
|      internal      | 内部访问。只限于本项目内访问，其他不能访问。         |
| protected internal | 内部保护访问。只限于本项目或是子类访问，其他不能访问 |

C#成员类型的可修饰及默认修饰符如下表：

C#成员类型的可修饰及默认修饰符如下表：

| 成员类型  | 默认修饰符 | 可被修饰符                                                |
| --------- | ---------- | --------------------------------------------------------- |
| enum      | public     | none                                                      |
| class     | private    | public、protected、internal、private、 protected internal |
| interface | public     | none                                                      |
| struct    | private    | public、internal、private                                 |



下面我就结合实例，讲一下public、private、protected、internal和protected internal的作用范围。

如下代码：

```c#
   1:  using System;
   2:  using System.Collections.Generic;
   3:  using System.Text;
   4:   
   5:  namespace AccessModifier
   6:  {
   7:      public class AccessModifierClass
   8:      {
   9:          public string GetPublicString()
  10:          {
  11:              return "Public String";
  12:          }
  13:   
  14:          protected string GetProtectedString()
  15:          {
  16:              return "Protected String";
  17:          }
  18:   
  19:          private string GetPrivateString()
  20:          {
  21:              return "Private String";
  22:          }
  23:   
  24:          internal string GetInternalString()
  25:          {
  26:              return "Internal String";
  27:          }
  28:   
  29:          protected internal string GetProtectedInternalString()
  30:          {
  31:              return "Protected Internal String";
  32:          }
  33:   
  34:          void AvailableAccessModifier()
  35:          {
  36:              this.GetPublicString();
  37:              this.GetPrivateString();
  38:              this.GetInternalString();
  39:              this.GetProtectedInternalString();
  40:              this.GetProtectedString();
  41:          }
  42:      }
  43:   
  44:      public class TestAccessModifierClass1
  45:      {
  46:          void AvailableAccessModifier()
  47:          {
  48:              AccessModifierClass item = new AccessModifierClass();
  49:              item.GetPublicString();
  50:              item.GetInternalString();
  51:              item.GetProtectedInternalString();
  52:          }
  53:      }
  54:   
  55:      public class TestAccessModifierClass2 : AccessModifierClass
  56:      {
  57:          void AvailableAccessModifier()
  58:          {
  59:              AccessModifierClass item = new AccessModifierClass();
  60:              item.GetPublicString();
  61:              item.GetInternalString();
  62:              item.GetProtectedInternalString();
  63:              base.GetProtectedString();
  64:          }
  65:      }
  66:  }
```

AccessModifierClass是我们的访问修饰符类，里面有五种访问修饰符方法，可见在AccessModifierClass类里面的AvailableAccessModifier()方法可以访问所有的方法。

在TestAccessModifierClass1类中的AvailableAccessModifier()方法只能访问public、Internal和Protected Internal方法。

TestAccessModifierClass2类继承自AccessModifierClass类，所以它的AvailableAccessModifier()方法可以访问public，internal,protected和protected internal方法。

在新建一个工程，且引用AccessModifierClass类的dll，代码如下：

```c#
   1:  using System;
   2:  using System.Collections.Generic;
   3:  using System.Text;
   4:  using AccessModifier;
   5:   
   6:  namespace AccessModifierApp
   7:  {
   8:      public class AccessModifierAppClass1 
   9:      {
  10:          void AvailableAccessModifier()
  11:          {
  12:              AccessModifierClass item = new AccessModifierClass();
  13:              item.GetPublicString();
  14:          }
  15:      }
  16:   
  17:      public class AccessModifierAppClass2 : AccessModifierClass
  18:      {
  19:          void AvailableAccessModifier()
  20:          {
  21:              AccessModifierClass item = new AccessModifierClass();
  22:              item.GetPublicString();
  23:              base.GetProtectedString();
  24:              base.GetProtectedInternalString();
  25:          }
  26:      }
  27:  }
```

