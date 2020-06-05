## 【java】类中使用getter和setter的优势

>  java有三大特性：封装，继承还有多态。

​		而今天，我来讲一下其中最重要的特性之一：**封装**。

​     首先，属性可用来描述同一类事物的特征，方法可描述一类事物可做的操作。封装就是把属于同一类事物的共性（包括属性与方法）归到一个类中，以方便使用。

​     1.概念：封装也称为信息隐藏，是指利用抽象数据类型将数据和基于数据的操作封装在一起，使其构成一个不可分割的独立实体，数据被保护在抽象数据类型的内部，尽可能地隐藏内部的细节，只保留一些对外接口使之与外部发生联系。系统的其他部分只有通过包裹在数据外面的被授权的操作来与这个抽象数据类型交流与交互。也就是说，用户无需知道对象内部方法的实现细节，但可以根据对象提供的外部接口(对象名和参数)访问该对象。

​     2.好处：(1)实现了专业的分工。将能实现某一特定功能的代码封装成一个独立的实体后，各程序员可以在需要的时候调用，从而实现了专业的分工。(2)隐藏信息，实现细节。通过控制访问权限可以将可以将不想让客户端程序员看到的信息隐藏起来，如某客户的银行的密码需要保密，只能对该客户开发权限。


​      而我们在设置变量的属性时，我们通常会对数据进行封装，这样就可以增加了数据访问限制，增加了程序可维护性。而实现方法就是：用private去修饰一个变量，然后再用setter方法去设置该变量的值，然后在用getter方法去调用该变量的值。

```java
public class Student{
		private String number;//学生学号
		private String name;//学生姓名
		private int grade;//学生成绩
		public Student(){
		}
		public String getNumber(){//用get方法得到学号(下同)
			return number;
		}
		public void setNumber(String number){//用set方法去设置学号(下同)
			this.number=number;
		}
		public String getName(){
			return name;
		}
		public void setName(String name){
			this.name=name;
		}
		public int getGrade(){
			return grade;
		}
		public void setGrade(int grade){
			this.grade=grade;
		}
    public static void main(String agrs[]){
	Student st=new Student();
	st.setNumber("010112233");
	st.setName("小明");
	st.setGrade(100);
	System.out.println("学号为："+st.getNumber()+","+"姓名为："+st.getName()+","+"成绩为："+st.getGrade()+"。");
  }
}
```

用setter来改变数据成员的值时，操作必须由这个对象自己来触发
用public来改变数据成员的值时，操作可以由任何对象来触发
这是面向对象的封装，总之就是自己的数据成员，只对自己可见，也只有自己才能改变其值



对象的封装性，
private的只有对象自己才可以访问，其他任何对象不行，包括它的子类和父类。安全性高，其他对象只能通过它的public方法，set,get来获取或设置原对象的private属性。
public其他对象可以访问，安全性就不高了。

 

**问题：在java 类中使用getter和setter的好处？**

定义为private 是为了实现数据的隐藏和封装；


而set get 方法提供了类与外部的接口；


在大型软件中这是很有必要的，它有利于代码的维护


*举个例子*，


一个父类有多个子类（甚至还有间接子类），程序代码中，子类是不能直接访问父类的private属性的；这时提供的set get方法是很有必要的


诚然，若将父类的属性声明为protected，在子类中就可以直接访问了，但是这种方法破坏了数据的隐藏和封装原则，关键是不利于代码的维护，
如果父类中的一个属性改名了，那么在子类中用到该属性名的代码，要发生大范围的修改，而前面的private，set，get方法就比较好，
对代码只需小范围的修改，一般都是这么用的，这是一个良好的编程习惯*/