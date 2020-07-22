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
  - 有返回值的方法，适合于任意一种方式的调用。
  - 没有返回值的方法，只适合于单独调用。
  - 方法有没有返回值，主要是看我们需不需要这个方法最终产生的数据，需要，就得有返回值，否则就没有返回值。
  - 注意事项：
    - 方法只能在类中定义，而方法中不能再定义方法。
    - 返回值类型必须和方法定义时的类型相同。
    
1.14 方法重载（overload）
   - 多个方法名称相同，但是参数列表不同。
   - 优势：只要记住一个方法名称，就可以实现多个类似的功能。
   - 方法重载与下列因素有关：
     - 参数个数不同
     - 参数类型不同
     - 参数的多类型顺序不同
   - 方法重载与下列因素无关：
     - 与参数名称无关
     - 与返回值类型无关
   - 也就是对于方法重载，方法名称必须一样，返回值类型必须一样，接收的参数类型和参数名称也必须一样。
   - 代码示例：
     ```
     package cn.itcast.day04.demo04;
     
     /**
      * 方法的重载
      */
     public class Demo01MethodOverload {
         public static void main(String[] args) {
             System.out.println(add(10, 20));
             System.out.println(add(10, 20, 30));
             System.out.println(add(10, 20, 30, 40));
             System.out.println(multiplication(5.5, 4));
         }
     
         public static int add(int a, int b) {
             System.out.println("调用两个参数的方法");
             return a+ b ;
         }
     
         public static int add(double a, int b, int c) {
             System.out.println("调用三个参数的方法");
             return (int) (a+ b + c) ;
         }
         public static int add(int a, int b, int c, int d) {
             System.out.println("调用四个参数的方法");
             return a+ b + c + d ;
         }
     
         //
         public static int multiplication(int a, int b) {
             return a * b ;
         }
         public static int multiplication(double a, int b) {
             System.out.println("乘法，调用两个参数的方法");
             return (int) a * b ;
         }
     
         // 方法重载的返回值类型必须相同
     //    public static double multiplication(int a, int b) {
     //        return a * b ;
     //    }
     
         // 方法重载的参数的名称必须相同
     //    public static int multiplication(int x, int y) {
     //        return x * y ;
     //    }
     }
     ```
     
1.15 **编译器优化（面试常问的问题）**
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

1.16 三种循环
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
  
  
1.17 数组
  - 特点
    - 数组是一种引用数据类型
    - 数组中的多个元素，类型必须统一
    - 数组的长度在运行期间不可以发生改变
  - 初始化
    - 在内存中分配一块空间，并向其中赋予一些默认值。
    - 两种常见的初始化方式：
      - 动态初始化（指定长度）
      - 静态初始化（指定内容）
  - 动态初始化数组的格式：`数据类型[] 数组名称 = new 数据类型[数组长度];`
  - 静态初始化数组的格式：`数据类型[] 数组名称 = new 数据类型[] {元素1, 元素2, ...};`
  - 使用建议：
    - 内容已经确定，使用静态初始化
    - 内容不确定，使用动态初始化
  - 动态初始化过程中，元素的默认值：
  
    数据类型|默认值
    |:---:|:---:|
    整型|0
    浮点型|0.0
    字符型|'\u0000'，这是一个不可打印的字符
    布尔类型|false
    引用类型|null
   
  - 静态初始化也有默认值的过程，只不过系统马上将默认值替换为大括号中具体的值。
  - **获取数组长度**
    - `array.length`
  - **数组长度在程序运行期间不可变。**
    
1.18 Java对于内存的管理
  1. 栈（stack）
    - 存放的都是方法中的局部变量，**方法运行时一定要在栈当中。**
    - 局部变量指的是方法的参数，或者是方法{}内部的变量，仅在作用域内起作用。
    - 基本数据类型全部存放于栈中。
    - **特点：栈内存的数据用完就释放。**
  2. 堆（heap）
    - **凡是new出来的东西，都存放在堆内存中。**
    - 堆内存使用完的东西会被jvm在合适的时机回收（gc）。
    - 堆内存存放的东西，都有默认值。规则如下：
    
      数据类型|默认值
      |:---:|:---:|
      整型|0
      浮点型|0.0
      字符型|'\u0000'，这是一个不可打印的字符
      布尔类型|false
      引用类型|null
        
  3. 方法区（Method Area）
    - **存放.class相关的信息，包含方法的信息。**
  4. 本地方法栈（Native Method Stack）
    - 与操作系统相关。
  5. 寄存器（pc Register）
    - 与CPU相关。
    
1.19 使用数组中常见的异常
  - 索引越界异常：ArrayIndexOutOfBoundsException
  - 空指针异常：NullPointerException
  
1.20 数组作为方法的参数
  - 传递进去的是数组的地址。因为数组是引用数据类型。变量保存的也是数组的引用地址。
  
1.21 数组作为方法的返回值
  - 任何数据类型都能作为方法的参数，也能作为方法的返回值。
  - 数组作为方法的返回值，返回的也是地址值。
  - 代码示例:
    ```
    package cn.itcast.day05.demo04;
    
    /**
     * 数组作为方法返回值，返回的也是地址
     */
    public class Demo02ArrayReturn {
        public static void main(String[] args) {
            int[] result = calculate(10, 20, 30) ;
            // 返回值也是地址，[I@58ceff1
            System.out.println(result);
            // sum is 60
            System.out.println("sum is " + result[0]);
            // avg is 20
            System.out.println("avg is " + result[1]);
        }
    
        /**
         *
         * @param a
         * @param b
         * @param c
         * @return
         */
        public static int[] calculate(int a, int b, int c) {
            int sum = a + b + c ;
            int avg = sum / 3 ;
            int[] ret = {sum, avg} ;
            return ret ;
        }
    }
    ```
1.22 面向对象的基本概念 
  - 类
    - 是一组相关**属性**和**行为**的集合。可以看成一类事物的模板。使用事物的属性特征和行为特征来描述该类事物。
    - **属性**：该事物的状态信息
    - **行为**：就是该事物能做啥
  - 对象
    - 是一类事物的具体体现。对象是类的一个实例。必然具备该类事物的属性和行为。
  - 对象与类的关系
    - 类是对一类事物的描述，是抽象的。
    - 对象是一类事物的实例，是具体的。
    - **类是对象的模板，对象是类的实体。**
    
1.23 定义类
  - 使用class关键字定义一个类。类名称的首字母都要大写。
  - 代码示例：
    ```
    public class Student {
        String name ;
        int age ;
    
        public void eat() {
            System.out.println("吃好吃的");
        }
    
        public void sleep() {
            System.out.println("睡觉");
        }
        
        public void study() {
            System.out.println("学习");
        }
    
    }
    ```
  - 类中可以定义变量，也可以定义方法。定义变量时，可以不用赋初值。
  
1.24 使用类
  1. 导包
     - 使用import从某一个路径下导入我们需要使用的类。如：`import cn.itcast.day06.demo01.Student;`，也可以这样写：`import cn.itcast.day06.demo01.*;`，`*`表示导入这个包下所有的类文件。
     - 在同一路径下，可以不用导入别的类文件，直接使用即可。
  2. 实例化
     - 类名 变量名 = new 类名() ;
  3. 使用
     - 获取成员变量和成员方法，使用点方式（与JavaScript类似）
     - 获取成员变量：实例.成员变量
     - 调用成员方法：实例.成员方法
  4. 代码示例：
     ```
        package cn.itcast.day06.demo01;
        
        public class Demo02Student {
        
            public static void main(String[] args) {
                // 实例化一个新对象
                // 对于在同一路径下的类文件而言，我们不需要导入，也可以使用。
                // 类名 变量名 = new 类名() ;
                Student stu = new Student() ;
                // 获取成员变量，使用点方式
                // 实例.成员变量
                // 没有给成员变量赋值，所有成员变量是默认值
                System.out.println(stu.name);  // null
                System.out.println(stu.age);  // 0
        
                // 给成员变量赋值
                stu.age = 18 ;
                stu.name = "张三" ;
                System.out.println(stu.name);  // 张三
                System.out.println(stu.age);  // 18
        
                // 调用成员方法
                stu.eat();
                stu.study();
                stu.sleep();
            }
        
        }
     ```
1.25 对象无论作为方法的参数，还是方法的返回值，实际上使用的都是这个对象的地址值。

1.26 局部变量和成员变量的区别
   - **定义的位置不同**
     - 局部变量：定义在方法内部 
     - 成员变量：定义在方法外部，直接定义在类中
   - **作用范围不同**
     - 局部变量：只能在方法内部使用，在方法外部不能使用 
     - 成员变量：整个类中都可以使用
   - **默认值不同**
     - 局部变量：没有默认值，如果想使用，必须手动赋值
     - 成员变量：如果没有赋值，会有默认值
   - **内存位置不一样**
     - 局部变量：位于栈内存，因为局部变量在方法内部，而方法是在栈内存中运行的，所以局部变量存储在栈内存中。
     - 成员变量：位于堆内存，因为成员变量直接定义在类中，而类被实例化以后，是存放在堆内存中的，所以成员变量存储在堆内存中。
   - **生命周期不同**
     - 局部变量：随着方法进栈而诞生，随着方法出栈而消失。
     - 成员变量：随着对象的创建而诞生，随着对象被垃圾回收而消失。
     
1.27 面向对象的三大特性——封装性
  - 封装性在java中的体现：
    - 方法就是一种封装
    - 关键字private也是一种封装
  - 使用private对成员变量进行修饰，使得我们不能直接设置和获取类中的成员变量，必须使用setter/getter方法。这样提高了数据的安全性，而在setter方法中，还可以对传入的数据进行限制，从而保证了数据的合理性。
  - 代码示例：
    ```
       package cn.itcast.day06.demo03;
       
       public class Person {
           private String name ;
           private int age ;
       
           public void setAge(int num) {
               if (num <= 100 && num > 0) {
                   age = num ;
               } else{
                   System.out.println("输入数据有误！！！！！！！！");
               }
       
           }
           public int getAge() {
               return age ;
           }
    
           public void setName(String str) {
               name = str ;
           }
           public String getName() {
               return name ;
           }
    
           public void show() {
               System.out.println("姓名: " + name + ", " + "年龄: " + age);
           }
       }

    ```
  - setter/getter的格式（Xxx表示首字母大写的成员变量名）：
    - `public void setXxx(参数) {}`
    - `public 类型 getXxx() {}`
  - 如果在类中定义有布尔值，则布尔值的getter方法的格式是:`public boolean isXxx() {}`，setter方法的格式没有变化。

1.28 this关键字
  - this用来区分局部变量和成员变量。
  - 原则：**谁调用这个包含this的方法，this就指向谁**
  - this一般是定义在类中的普通方法中，所以哪个实例调用这个方法，方法中的this就指向哪个实例。
    ```
       package cn.itcast.day06.demo04;
       
       public class Person {
           String name ;
       
           public void greeting(String name) {
               // this指向当前的调用对象
               System.out.println(name + " hello, i am " + this.name);
               System.out.println("当前的this指向：" + this);
           }
       }
    
      package cn.itcast.day06.demo04;
      
      public class Demo01Person {
      
      
          public static void main(String[] args) {
              Person person = new Person() ;
              person.name = "jack" ;
              person.greeting("smith");
              // smith hello, i am jack
              // 当前的this指向：cn.itcast.day06.demo04.Person@3b81a1bc
              // person指向：cn.itcast.day06.demo04.Person@3b81a1bc
              System.out.println("person指向：" + person);
          }
      }
    ```
    - 从上述代码的输出中，我们可以看出，this和person指向的是同一个对象。
    
1.29 构造方法
  - 在实例化一个新的对象的时候，实际上调用的是构造方法。
    ```
       package cn.itcast.day06.demo04;
       
       public class Student {
           public Student() {
               System.out.println("构造方法执行了！！！！！！！");
           }
       }
    
       public class Demo02Student {
           public static void main(String[] args) {
               // 构造方法执行了！！！！！！！
               Student stu = new Student() ;
           }
       
       }
    ```
  - 从上面的输出中，可以看出，在实例化过程中，确实会调用构造方法。
  - 构造方法的定义：`public 类名称() {方法体}`
  - 构造方法注意事项：
    - 构造方法的名称必须与类名相同
    - 构造方法不要写返回值类型，连void也不要写
    - 构造方法内部，不能写return
    - 如果没有显式的声明一个构造方法，那么编译器会加上一个构造方法
    - 构造方法可以进行重载。
    - 代码示例：
      ```
        package cn.itcast.day06.demo04;
        
        public class Student {
        
            private String name ;
            private int age ;
        
            // 构造方法可以进行重载
            public Student() {
                System.out.println("构造方法执行了！！！！！！！");
            }
        
            public Student(String name, int age) {
                this.name = name ;
                this.age = age ;
            }
        
            public void setName(String name) {
                this.name = name;
            }
            public String getName() {
                        return this.name ;
            }
      
            public void setAge(int age) {
                this.age = age;
            }
            public int getAge() {
                return this.age ;
            }
        }
        
        package cn.itcast.day06.demo04;
        
        public class Demo02Student {
            public static void main(String[] args) {
        
                Student stu = new Student("张三", 25) ;
        
                System.out.println("姓名：" + stu.getName());
                System.out.println("年龄：" + stu.getAge());
                System.out.println("===============");
        
                // 由于构造方法可进行重载，所以不传入参数的时候，调用的是无参的构造方法
                Student stu2 = new Student() ;   // 构造方法执行了！！！！！！！
        
            }
        
        }
      ```

1.30 构造一个标准的类
  - 构造一个标准的java类，包含四部分内容：
    1. 所以的成员变量使用private进行修饰。
    2. 为每一个成员变量书写getter/setter方法
    3. 编写一个无参数的构造方法
    4. 编写一个全参数的构造方法
  - 符合这样的标准的类，被称为是Java Bean。
  - 代码示例
    ```
        public class Student {
        
            private String name ;
            private int age ;

            public Student() {}
        
            public Student(String name, int age) {
                this.name = name ;
                this.age = age ;
            }
        
            public void setName(String name) {
                this.name = name;
            }
        
            public void setAge(int age) {
                this.age = age;
            }
        
            public String getName() {
                return this.name ;
            }
        
            public int getAge() {
                return this.age ;
            }
        }

    ```
    
1.31 static 关键字
  - 一旦某个方法或者成员变量被static修饰，那么这个方法或者成员变量就不属于某个实例本身，而是属于这个类。多个对象共享这个一个数据。
  
    