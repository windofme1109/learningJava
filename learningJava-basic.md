### 1. 基础语法
1.1 标识符规则
  - 只能使用0-9、a-z、A-Z、_和$
  - 不能以数字开头
  - 标识符不能是关键字
  - 类标识名称使用大驼峰命名方式
  - 方法和变量的名称使用小驼峰命名方式

1.2 常量
  - 指的是在程序运行过程中，不变的量。例如输出一个字符串常量：`System.out.println("tiger") ;`，`"tiger"`就是一个字符串常量。
  - 分类
    - 字符串常量
    - 整数常量
    - 浮点数常量
    - 字符常量
    - 布尔常量，true/false
    - 空常量，null
  - 字符常量有且只有一个字符，不能为空，也不能多于一个字符。例如：`System.out.println('a') ;`，就是正确的，而`'ab'`、`''`都是错误的。
 
1.3 数据类型
  - 基本数据类型
    - 整数型
      - byte
      - short
      - int
      - long
    - 浮点型
      - float
      - double
    - 字符型
      - char
    - 布尔型
      - boolean
  - 表格形式总结：

  数据类型|关键字|内存占用|取值范围
  :---:|:---:|:---:|:---:
  字节型|byte|1个字节|-128-127
  短整型|short|2个字节|-32768-32767
  整型|int|4个字节|-2^31~2^31-1
  长整型|long|8个字节|-2^63~2^63-1
  单精度浮点型|float|4个字节|1.4013E-45~3.4028E+38
  双精度浮点型|double|8个字节|4.9E-324~1.977E+308
  字符型|char|2个字节|0-65536
  布尔型|boolean|1个字节|true / false
  
  - 引用数据类型
    - 字符串
    - 数组
    - 类
    - 接口
  - 注意：
    - 字符串不是基本数据类型，而是引用类型。
    - 浮点型可能只是一个近似值，并非精确值。
    - 数据范围与字节数不一定相关。float表示的范围比long更加广泛，但是float占据4字节，long是8字节。
    - 浮点数中默认类型是double。如果一定要用float，需要加上一个F作为后缀。
    - 整数的默认类型是int，如果一定要使用long类型，那么就加一个L作为后缀。

1.4 变量
  - 程序运行期间，内容可以发生改变的量。
  - 变量的定义：
    - 数据类型 变量名 = 数据值 ;
1.5 创建变量需要注意的问题
  - 创建多个变量，变量名称不能重复。
  - 对于float和long类型来说，字母后缀F和L不要丢掉。
  - 使用byte和char类型的变量，注意数据的范围。
  - 没有进行赋值的变量不能直接使用。一定要赋值以后才能使用。
  
1.6 数据类型转换
  - 自动类型转换（隐式）
    - 特点：代码不需要进行特殊处理，自动完成。
    - 规则：数据范围从小到大。即int --> long，float --> double，long --> float。
  - 强制类型转换
    - 特点：代码需要进行特殊格式处理，不能自动完成
    - 格式：范围小的类型 范围小的变量名 = (范围小的类型) 原本范围大的数据;
    - 注意事项：
      - 强制类型转换一般不推荐使用，因为有可能发生精度损失、数据溢出。
      - byte/short/char这三种类型都可以发生数学运算，例如+。
      - byte/short/char这三种类型都可以发生数学运算，例如+。这三种类型在运算时，都会被首先提升为int类型，然后进行运算。
      - boolean类型不能发生数据类型的转换。
    - 示例代码:
    ```
      public class Demo02DataType {
        public static void main(String[] args) {
          //		强制类型转换
    		int num1 = (int) 100L ;
            //		100
    		System.out.println(num1) ;
    
    		char aa = 'A' ;
            //      66
    		System.out.println(aa + 1) ;
    
    		byte num2 = 40 ;
    		byte num3 = 50 ;
            //		byte + byte --> int + int = int
            //		所以，两个byte相加（或者其他数学运算），使用int接收结果
    		int num4 = num2  + num3 ;
    		System.out.println(num4) ;
    
    		short num5 = 60 ;
            //		short + byte --> int + int = int
            //		由于num5 + num2没有超过short范围，所以可以使用强制类型转换，将int转换为short
    		short num6 = (short) (num5 + num2) ;
    		System.out.println(num6) ;
    	}
      }
    ```
    
1.7 算数运算符-加号
  - 数值 —————— 数学运算
  - char —————— 计算之前，先辈转换成int类型，然后再进行计算。
  - 字符串 ————— 加号表示连接操作，任何数据类型和字符串进行连接时，结果都会变成字符串。
  - 代码示例：
  ```
  public class Demo05Plus {
    public static void main(String[] args) {
		// 使用+进行字符串连接操作
		String str1 = "java" ;
		System.out.println(str1) ;
		// 任何数据类型和字符串进行连接时，结果都会变成字符串
		System.out.println(str1 + 20) ;  // java20
		System.out.println(str1 + 20 + 50) ;  // java2050
		
		char c = 'A' ;
		System.out.println(str1 + c) ;  // javaA
    }
}
  ```
1.8 算数运算符-自增和自减
  - 自增：++
  - 自减：--
  - 使用方式：可以放在变量前：`++a`，也可以放在变量后：`a--`。
  - 单独使用：不和其他任何操作混合，自己是一个单独的步骤。
  - 混合使用：与其他操作混合，如与赋值操作混合，打印操作混合等。
  - 注意事项：
    - 单独使用，前++与后++没有任何区别，最终的结果都是让变量加1。
    - 混合使用，有**重大区别**：
      - 前++，那么变量**立刻加1**，然后拿着结果进行使用，即**先加后用**。
      - 后++，那么首先使用变量原来的数值，**然后在让变量进行加1**，即**先用后加**
  - 代码示例：
  ```
    public class Demo06Operator {
	    public static void main(String[] args) {
		// 单独使用
    		int num1 = 10 ;
    		num1++ ;
    		// 11
    		System.out.println(num1) ;
    		int num2 = 11 ;
    		++num2 ;
    		// 12
    		System.out.println(num2) ;
    		
    		System.out.println("========================") ;
    		
    		// 混合使用
    		int num3 = 20 ;
    		// 后++，就是先进行赋值操作，然后执行加1操作
    		int ret1 = num3++ ;
    		// 20
    		System.out.println(ret1) ;
    		// 21
    		System.out.println(num3) ;
    		
    		System.out.println("======================") ;
    		
    		int num4 = 30 ;
    		// 前++，就是先执行加1，然后进行赋值操作
    		int ret2 = ++num4 ;
    		// 31
    		System.out.println(ret2) ;
    		// 31
    		System.out.println(num4) ;
	   }
    }
  ```
1.9 赋值运算符
  - 基本赋值运算符：=
  - 复合赋值运算符
    - +=
    - -=
    - *=
    - %=
  - 复合运算符，会自动完成数据类型的转换
1.10 比较运算符

  运算符|含义
  :--:|:--:|
   ==|相等
   >|大于
   <|小于
   >=|大于等于
   <=|小于等于
   !=|不等于
  
1.11 逻辑运算符
逻辑运算符|含义
  :--:|:--:|
   &&|与
   \|\||或
   !|非
1.12 三目运算符
  -  数据类型 变量名称 = 条件判断 ? 表达式A : 表达式B ;
  - 条件为true，表达式A赋值给左边的变量
  - 条件为false，表达式B赋给左边的变量
  - 注意事项：
    - 必须同时保证表达式A和表达式B都符合左侧数据类型的要求
    - 三元运算符的结果必须被使用。
1.13 方法
  - 若干语句的功能集合。
  - 将一部分经常使用的代码封装起来，供其他部分调用。这样做的好处是：
    - 避免书写重复代码，精简程序。
    - 方便阅读代码。
    - 方便使用。
  - 格式：
  ```
   访问修饰符 返回值类型 方法名(参数列表) {
       方法体
   }
  ```
  - 名称解释
    - 访问修饰符：方法允许被访问的权限范围，可以是public，private，protected，还可以忽略。public可以被任意代码调用。
    - 返回值类型：可以是int，float，byte等一些数据类型，还包括自定义的一些类。没有返回值使用void。
    - 参数列表：方法需要的参数。
  - 代码示例：
  ```
    public class Demo11Method {
    	public static void main(String[] args) {
    		// 调用一个方法
    		seller() ;
    	}
	
    	// 定义一个方法
    	public static void seller() {
    		System.out.println("apples") ;
    		System.out.println("bananas") ;
    		System.out.println("oranges") ;
    		System.out.println("water") ;
    	}
}
  ```
  - 调用方式：
    - 单独调用
    - 打印调用
    - 赋值调用
    
1.14 **编译器优化（面试常问的问题）**
  - 对于byte/char/short三种类型来说，如果右侧赋值的数值没有超过范围，那么在编译过程中，会自动隐含的为我们补上一个(byte)(char)(short)。
  - 如果没有超过左侧的范围，编译器补上强转。
  - 如果右侧超过了左侧范围，那么编译器直接报错。
  - 代码示例：
  ```
    public class Demo12Notice {
    	public static void main(String[] args) {
    		// 没有超过byte的范围，所以会自动进行转换
    		// int --> byte
    		byte num1 = 45 ;
    		System.out.println(num1) ;
    		
    		// 超过了byte的范围，所以会报错：不兼容的类型: 从int转换到byte可能会有损失
    		// byte num2 = 250 ;
    		// System.out.println(num2) ;
    	}
     }
  ```
  - 在给变量进行赋值的时候，如果右侧的表达式当中全部都是常量，没有变量，那么在编译器过程中，会直接将这些常量表达式计算的得到结果。例如：`short ret = 5 + 8 ;`，等号右侧全部都是常量，没有任何变量参与运算，那么编译之后，得到的.class字节码文件中相当于就是：`short ret = 13 ;`，右侧的常量结果数值，没有超过左侧范围，所以正确。这被称为“编译器的常量优化”。**注意**，一旦表达式中有变量参与，就不能进行这种优化了。
  ```
  public class Demo13Notice {
	public static void main(String[] args) {
		short num1 = 10;
		
		short a = 5 ;
		short b = 8 ;
		
		// a 是short，b是short，那么a+b实际上是：int + int，所以要使用int进行接收
		// 使用short接收，就会报错：不兼容的类型: 从int转换到short可能会有损失
		// short ret = a + b ;
		int ret = a + b ;
		
		System.out.println(ret) ;
		
		// 使用常量，直接编译过程完成计算和转换
		short ret2 = 10 + 15 ;
		System.out.println(ret2) ;
		
		// 变量和常量的混合，会报错：不兼容的类型: 从int转换到short可能会有损失
		// short ret3 = 1 + a + 5 ;
		// System.out.println(ret3) ;
		
	}
}
  ```

1.15 三种循环
  - for
  - while
  - do while
  - 代码示例：
  
   ```
        public class Demo12HundredSum {
            public static void main(String[] args) {
                int sum = 0 ;
                // 使用for循环
                for (int i = 1; i <= 100; i++) {
                    if (i % 2 == 0) {
                        sum += i ;
                    }
                }
                System.out.println("for 循环") ;
                // 2550
                System.out.println(sum) ;
                int sum2 = 0 ;
                int j = 1 ;
                // 使用while循环
                while (j <= 100) {
                    if (j % 2 == 0) {
                        sum2 += j ;
                    }
                    
                    j++ ;
                }
                System.out.println("while 循环") ;
                // 2550
                System.out.println(sum2) ;
                int sum3 = 0 ;
                int k = 1 ;
                // 使用do while循环
                do {
                    if (k % 2 == 0) {
                        sum3 += k ;
                    }
                    k++ ;
                } while (k <= 100) ;
                
                System.out.println("do while 循环") ;
                // 2550
                System.out.println(sum3) ;
            }
     }
   ```
    
  - 三种循环的区别
    - `for`、`while`是先判断，条件满足才进入循环，而`do while`则是先循环后判断。所以，当条件不满足时，`for`、`while`循环次数是0，而`do while`循环次数是1。
    - 循环次数确定时，比如遍历数组，这种情况下，使用`for`循环更加方便，而循序次数不确定，比如说二分法查找元素，使用`while`循环更加方便。
    - `do while`用的比较少。
  
  