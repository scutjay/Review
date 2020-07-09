复习提纲

[TOC]



### 一、 Java基础

#### 1. Java的定义



​	Java是面向对象的语言。对面向对象的语言来说，一切皆为对象。与面向过程的语言相比，面向对象的语言更重视对象自身状态的变化和对象间的影响， 而面向过程的语言更重视事务执行的先后顺序。

#### 2. 四大特性

- 抽象，对同一类事物特征的抽取、归纳、总结，是Java面向对象的基础。
- 封装，封装好的特征或方法只能通过暴露出来的接口使用，目的是保证抽象出来的特征和方法的安全性。
- 继承（“is-a”），在父类可继承的特征和方法的基础上，增加额外的部分，继承（extend）只能唯一，实现（interface）不唯一，目的是实现代码的复用。继承的初始化顺序：父类属性->父类构造方法->子类属性->子类构造方法。
- 多态，表现形式有：方法重写、方法重载、接口实现、父类继承，方法重写时参数返回值必须一样，方法重载是参数可以不同，但是返回值必须一样，目的是使代码更加灵活。方法重写的调用顺序：子类方法->父类方法。

#### 3. 保留字

##### public/protected/private/default



* |           | 同一个类 | 同一个包 | 不同包的子类 | 不同包的非子类 |
| :-------: | :------: | :------: | :----------: | :------------: |
|  public   |    √     |    √     |      √       |       √        |
| protected |    √     |    √     |      √       |                |
|  default  |    √     |    √     |              |                |
|  private  |    √     |          |              |                |
- public: 可以跨包访问
- protected：同包可访问，不同包子类可访问
- default：同包可访问
- private：同类可访问

##### final

- 修饰类：不可被继承。
- 修饰接口：不可用于修饰接口。
- 修饰方法：不可被重写。
- 修饰属性：初始定义时必须有值，不可被修改。
- 修饰变量：只能被赋值一次（初始或后来），不可被修改。

##### static

- 修饰内部类：不需要创建外部类也可被外部使用。
- 修饰方法：不需要创建对象亦可使用，不能使用非类变量。
- 修饰变量：类变量，不需要创建实例对象亦可使用，线程共用，存在方法区。

##### super关键字

- super.age 访问父类属性。
- super.print() 访问父类方法。
- super() 调用父类构造方法，必须在构造方法首先执行。

#### 4. 内部类（@动手试试@）

内部类的种类如下：
- 成员内部类
- 静态内部类
- 方法内部类
- 匿名内部类

内部类的作用如下：
1. 内部类提供了更好的封装，可以把内部类包裹在外部类之内，不允许其他类访问。
2. 内部类可以使用外部类的所有数据，包括私有数据。
3. 某些场景下内部类更方便。

#### 5. 重写（override）和重载（overload）

- 复用父类或接口的方法定义，重新实现的做法叫做重写。
- 共用方法名，有不同的输入参数和实现的做法叫做重载，重载的返回值类型必须相同。
- 构造方法不能重写，可以重载。

#### 6. Java跨平台管理

​	由于操作系统的指令集不完全一致，所以Java有不同版本的JVM对应于不同的操作系统，运行时通过JVM调用操作系统提供的指令集，对程序本身包装成接口。

#### 7. String、StringBuilder、StringBuffer

​	String是内容不可变的字符串，会存放在方法区的常量池中，而StringBuffer和StringBuilder是可变的。

​	StringBuffer和StringBuilder都继承自AbstractStringBuilder，前者线程安全，效率较低，后者线程不安全，效率较高。

#### 8. Java中的集合

Java中的集合分为value（Collection）、key-value（Map）两种，Set是Map的一种。

#### 9. HashMap和HashTable的区别

1. 两者都可以用来修饰key-value的数据。
2. 前者key和value可放null，后者不行。
3.  前者线程不安全，效率较高，后者线程安全，效率低。
4. 使用ConcurrentHashMap可以同时得到线程安全且效率高。

### 二、 JVM基础



### 三、 数据结构与算法

#### 数据结构

数据结构是将数据以一定布局储存起来的方法，根据不同的储存方式，不同的数据结构就有了不同的存取特点。

##### 1. 数组

数组是最简单、使用最广泛的数据结构。在创建数组时，会在内存中申请连续的储存空间，所以对于数组来说，插入节点和删除节点都是低效的。

为什么大多数语言数组序号都是从0开始呢？因为序号表明的是偏移的单位。

在Java中，二维数组的空间开销是一维数组的10倍。

常见问题1：查找数组中第二小的元素。只需遍历一次，需要两个整型变量firstMin、secondMin，刚开始的时候将第一二个元素中较小的放置在firstMin，较大的放置在secondMin。然后每找到比firstMin小的就把firstMin放置到secondMin，将找到的值放到firstMin，如果找到比firstMin大但是比secondMin小的就放到secondMin。这样遍历完第一次之后secondMin的就是第二小的元素。复杂度为o(n)。

常见问题2：找到数组中第一个不重复出现的整数。双循环，外循环遍历0~size-2，内循环遍历1~size-1。复杂度为o(n^2)。

##### 2. 队列

队列的特点是先进先出（FIFO）。

常见问题1：用队列表示栈，用栈表示队列。记录队列元素数量n，前面n-1个元素输出后重新插入队列，这样就可以拿到最后进入队列的元素和大小为n-1的队列；每次取值时将后入的n-1个元素弹出到辅助栈，这样就可以取到最先进入栈、被压在栈底的元素。

常见问题2：对队列的前k个元素倒序。需要用到一个栈和一个新的队列，将前k个元素推入栈再弹出到新的队列，再将原队列剩余的元素输出到新队列。

##### 3. 栈

栈的特点是先进后出（FILO）。

常见问题1：前缀表达式，后缀表达式。了解了这两个表达式的定义，应该很容易。

常见问题2：判断表达式是否括号平衡。遇到右括号加一，遇到左括号减一，结果为0就是括号平衡。

##### 4. 树

树形结构是一种层级式的数据结构，由顶点（节点）和连接它们的边组成。树类似于图，但区分树和图的重要特征是树中不存在环路。二叉树和二叉搜索树是最常见的树。

##### 4.1. N元树

N元树是最初级的树，每个父节点下有不定数量的子节点。

##### 4.3. 二叉树

二叉树中每个节点下最多有两个子节点，尽管易于实现，却不能有实际的价值。

常见问题1：求二叉树的高度。

常见问题2：在二叉搜索树中查找第K个最大值。

常见问题3：查找与根节点距离K的节点。

常见问题4：在二叉树中查找给定节点的祖先节点。

##### 4.4. 二叉搜索树

左节点要小于右节点。它既有链表的快速插入与删除操作的特点，又有数组快速查找的优势，文件系统和数据库系统一般会采用这种数据结构进行高效率的排序与检索操作。

![img](https://bkimg.cdn.bcebos.com/pic/8644ebf81a4c510f0b3dafdf6359252dd52aa57e?x-bce-process=image/watermark,g_7,image_d2F0ZXIvYmFpa2U4MA==,xp_5,yp_5)

##### 4.7. 平衡二叉搜索树（Balance Tree）

任何节点的左右子树的高度差都小于等于1。在对节点进行插入与删除的时候，除了要遵循二叉搜索树的规则，还需要根据左右子树的高度进行调整重新达到平衡。

调整平衡的方式共有四种情况：分别是LL，LR，RR，RL。

（1）LL型

![img](https://img-blog.csdn.net/20151031212103843?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

（2）LR型

![img](https://img-blog.csdn.net/20151031212033483?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

（3）RR型

![img](https://img-blog.csdn.net/20151031210747198?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

（4）RL型

![img](https://img-blog.csdn.net/20151031211108782?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

常见问题：增加或删除节点后，如何调整平衡二叉搜索树才能使之重新回到平衡

##### 4.8. B树

B树

##### 4.2. 2-3树

2-3树是最简单的B-树（或-树）结构，其每个飞叶节点都有两个或三个子节点，而且所有叶节点都在同一层上。2-3树不是二叉树，其节点可拥有3个孩子。不过，2-3树与满二叉树相似。高位h的2-3树宝内涵的节点数大于等于高度为h的满二叉树的节点数，即至少有2^h-1个节点。

##### 4.5. AVL树

##### 4.6. 红黑树

##### 4.9. B+树



##### 5. 堆

##### 6. 散列表

##### 7. 链表

##### 8. 图

##### 9. 跳表

##### 10. Trie树（前缀树/字典树）

#### 算法设计

##### 1. 递归

求5的10次方

```java
public class Test {
    @Test
    public void test() {
        assertEquals(1024, multiple(2, 10));
    }
    
    public static long multiple(long base, long power) {
        return power == 0 ? 1 : base * multiple(base, power - 1);
    }
}
```

##### 2. 排序（冒泡排序、快排）

冒泡排序

```java
public class Test {
    public static int[] bubbleSort(int[] elements) {
        for (int i = 0; i < elements.length - 1; i++) {
            for (int j = i + 1; j < elements.length; j++) {
                if (elements[i] > elements[j]) {
                    elements[i] = elements[i] + elements[j];
                    elements[j] = elements[i] - elements[j];
                    elements[i] = elements[i] - elements[j];
                }
            }
        }

        return elements;
    }

    @Test
    public void test() {
        int[] ints = {6,4,5,9,2,10,7,1};
        ints = bubbleSort(ints);
        assertEquals(6, ints[4]);
    }
}
```

快速排序

![img](https://bkimg.cdn.bcebos.com/pic/b7003af33a87e950707fdf2110385343fbf2b416?x-bce-process=image/watermark,g_7,image_d2F0ZXIvYmFpa2U3Mg==,xp_5,yp_5)

```java
public class Test {
    public static void quickSort(List<Integer> list, int leftIdx, int rightIdx) {
        if (leftIdx >= rightIdx)
            return;

        boolean moveLeft = true;
        int left = leftIdx, right = rightIdx;
        while (left < right) {
            if (list.get(left) > list.get(right)) {
                exchange(list, left, right);
                moveLeft = !moveLeft;
            } else {
                if (moveLeft)
                    left++;
                else
                    right--;
            }
        }

        quickSort(list, leftIdx, left - 1);
        quickSort(list, left + 1, rightIdx);
    }

    public static void exchange(List<Integer> list, int leftIdx, int rightIdx) {
        list.set(leftIdx, list.get(leftIdx) + list.get(rightIdx));
        list.set(rightIdx, list.get(leftIdx) - list.get(rightIdx));
        list.set(leftIdx, list.get(leftIdx) - list.get(rightIdx));
    }

    @Test
    public void test() {
        List<Integer> list = new ArrayList<>();
        Random random = new Random();
        for (int i = 0; i < 40; i++) {
            list.add(random.nextInt(500));
        }
        quickSort(list, 0, list.size() -1);

        for (Integer integer : list) {
            System.out.print(integer + " ");
        }
    }
}
```



##### 3. 二分查找

##### 4. 搜索

##### 5. 哈希算法

##### 6. 贪心算法

##### 7. 分值算法

##### 8. 回溯算法

##### 9. 动态规划

##### 10. 字符串匹配算法

### 四、 设计模式



### 五、 并发处理



### 六、 程序调优

#### 1. JVM方法内联

方法内联，是指JVM在运行时会将调用次数达到一定阈值的方法调用替换为方法本身，从而消除调用成本，并为接下来进一步的代码优化提供基础，是JVM的一个重要优化手段之一。

[link](https://www.jianshu.com/p/ae28d199e612)（要自己验证）

#### 2. 尽量多用synchronized修饰代码块，而不是用synchronize修饰方法，因为后者会将该对象锁住，不能调用该对象的其他方法。

#### 3. 创建HashMap的时候，构造方法实际上是可以指定创建出来的Map的大小的，在可以预测大小的情况下，建议使用

```java
new HashMap(int initialCapacity, float loadFactor)
```

#### 4. 可以使用位移运算代替乘除法,更快更高效
```
int a = 8*4 => int a = 8 << 2
int b = 16/2 => int b = 16 >> 1
```



### 七、 Spring



### 八、 计算机网络



### 九、 数据库（MySQL、Oracle）



### 十、 分布式开发运维



### 十一、 Linux

