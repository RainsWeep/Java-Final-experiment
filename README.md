# 计181 张博元 2018310730
Java最后一次实验，完善学生选课系统。

## 一、实验目的 
分析学生选课系统的数据结构并且将文件中的数据以字符串形式读出；使用GUI窗体及其组件设计窗体界面让数据可视性更强同时完成读取和写入的功能；完成学生选课过程业务逻辑编程，实现选课退课开课的功能；基于文件保存并读取数据，新建文本文件，将文本文件中的数据在GUI中显示；处理异常，防止文件中出现空白字符。



## 二、实验要求 
1、内容：设计GUI窗体，支持学生注册、课程新加、学生选课、学生退课、打印学生选课列表等操作。
2、基于事件模型对业务逻辑编程，实现在界面上支持上述操作。
3、针对操作过程中可能会出现的各种异常，做异常处理
4、基于输入/输出编程，支持学生、课程、教师等数据的读写操作。
5、基于Github.com提交实验，包括实验SRC源文件夹程序、README.MD实验报告文档。



## 三、实验过程 
调用之前的学生选课系统的源代码和选课系统GUI的代码，在此基础上添加文件读取和写入操作。新建New Exception类用于排除文本文件空字符异常。在Gui类中将需要的文本读取和写入代码加入其中，在实例化Majorattribute类的参数时，通过文本读取的方法，转化为字符串，以“,”分隔后按顺序写入Majorattribute类的实例化中，在Gui类执行时调用，用以替代在代码内实例化的操作。在设置学生姓名、学号以及各个数据后，单击“确定”键，在GUI中的文本框得到数据的实例化体现，同时应用文件写入代码，将字符串写入文本文件中。


## 四、流程图 
![text](https://github.com/RainsWeep/Java-Final-experiment/blob/master/%E6%9C%AA%E5%91%BD%E5%90%8D%E6%96%87%E4%BB%B6(9).png)



## 五、核心代码和注释 
```javascript
	JLabel label1;JLabel label2;JLabel label3;JLabel 	label4,label5;JLabel label6;//定义标签
	JButton button1,button2;//定义按钮
	TextArea ta1,ta2;//定义显示文本框
  JTextField t1,t2,t3,t4,t5,t6,t7,t8;//定义输入文本框
	CheckboxGroup cbg;//定义选择组
	JComboBox b1;JComboBox b2;JComboBox b3;JComboBox b4;JComboBox b5;//定义下拉菜单
	JCheckBox c1,c2,c3;//定义可选择选项
		super("选课系统");//设置窗口的名字
		label1=new JLabel("请输入个人信息和所选课程，完成后单击确定。           ");//输入标签显示的信息
		ta1=new TextArea(17,35);//设置显示文本框长度
		ta2=new TextArea(17,35);
		button1=new JButton("确定");//设置按钮名字
	t2=new JTextField("",10);//设置输入文本框长度
	setBounds(600,300,625,600);//设置窗口出现位置和大小
		c.setBackground(Color.white);//设置背景为白色
		c.setLayout(new FlowLayout(FlowLayout.LEFT));//设置布局，流式布局，向左对齐		
c.add(label2);//添加标签
	c.add(t1);//添加可输入文本框
		c.add(new Checkbox("男", cbg, true)); 
	c.add(new Checkbox("女", cbg, false));//调用CheckboxGroup，选择男女
		c.add(b1);c.add(b2);c.add(b3);//调用JCombobox，设置下拉菜单
		c.add(label5);c.add(c1);c.add(c2);c.add(c3);//调用JCheckbox，设置选项
		button2.addActionListener(this);//调用按钮    	Majorattribute p = null;
	    	Majorattribute q = null;
	    	Majorattribute r = null;
	    	Students students = null;
	    	Majorattribute majorattribute = null;
	    	p  = new Majorattribute("线代", "571", "教102","2.5","4.0");
	    	q  = new Majorattribute("高数", "341", "教302","3.0","3.0");
	    	r  = new Majorattribute("Java", "122", "教204","1.5","5.0");
			//调用Majorattribute类、Students类，实例化三个课程属性
    	if(e.getSource()==button1)
				ta1.append("姓名："+t1.getText()+"\n"+
				"学号："+t2.getText()+"\n"+"性别："
				+cbg.getSelectedCheckbox().getLabel()+
				"\n"+"生日："+b1.getSelectedItem()+b2.getSelectedItem()
				+b3.getSelectedItem()+"\n");
	    	//输入信息后，判断语句设置点击Button1之后的操作
	    			if(c1.isSelected() && e.getSource()==button1)
					ta1.append( "课程：" + c1.getLabel()+" "+p.toString()+"\n");
					students = new Students(t1.getText(),t2.getText(),cbg.getSelectedCheckbox().getLabel(),p);
			//输入信息后，判断语句设置选择了选项c1并且点击Button1之后的操作，同时调用students类，将信息录入
			if(e.getSource()==button4){
				System.exit(0);
			}
			//点击Button4后，设置退出
			if(e.getSource()==button3)
				ta2.append("\n");
				majorattribute = new Majorattribute(t4.getText(),t5.getText(),
						t6.getText(),t7.getText(),t8.getText());
				//输入信息后，判断语句设置点击Button3之后的操作，同时调用Majorattribute类，将信息录入
package Final;

public class NewException extends Exception{
	public NewException(){
 	}
	public NewException(String str){ 
            super(str);
 	}
}
//设置新的Exception类，用于排除文本内空字符
File file=new File("C:\\Users\\18301\\Desktop\\课程信息.txt");
		    try {
		        FileInputStream in=new FileInputStream(file);
		        // size  为字串的长度 ，这里一次性读完
		        int size=in.available();
		        byte[] buffer=new byte[size];
		        in.read(buffer);
		        in.close();
		        str=new String(buffer,"GB2312");
		    } catch (IOException e1) {
		        // TODO Auto-generated catch block
		        e1.printStackTrace();
		    }
		    //打开文件，读取信息，同时排除文本空字符异常
					StringBuffer s_2=new StringBuffer();
					s_2.append(students);
					s_2.append(p);
					try {
						FileWriter fw=new FileWriter("C:\\Users\\18301\\Desktop\\test.txt");
						fw.write(s_2.toString() + "\n");
						fw.close();
						} 
					catch (IOException n) 
						{
						n.printStackTrace();
						}
					//将students类的参数写入文本文件

```

## 六、运行截图


GUi截图：![text](https://github.com/RainsWeep/Java-Final-experiment/blob/master/1574867401(1).png)




被读取的文本文件《课程信息》的截图：![text](https://github.com/RainsWeep/Java-Final-experiment/blob/master/1574867426(1).png)


被写入的文本文件《text》的截图：![text](https://github.com/RainsWeep/Java-Final-experiment/blob/master/1574867439(1).png)



## 七、编程感想
这是本学期最后一次实验，综合了前几次实验的功能，将需要的方法集于一炉，形成了最终的程序，选课系统的功能得到了完善与补充。我经历了老师给的例子打不开、GUI显示异常、无法获取数据等等问题，但我一一解决了，通过不断地尝试，最终终于调试出了合适的GUI界面来承载实验二的选课系统的功能，虽然做的GUI仍不漂亮也还有小bug，但是确实是比曾经的自己有所进步。
我还会继续完善我的Java知识储备，达到学以致用。
