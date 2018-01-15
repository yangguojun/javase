项目实战

知识总结

卡尔信息图书管理系统

Books.java

package com.carlinfo.dao;

/\*\*

\* @authoryangguojun

\* 图书集合信息

\*/

public class Books {

// 名称

String \[\]name= new String\[50\];

// 是否借出 0 已经借出。1 可借

int \[\]state= newint\[50\];

// 借出日期

String \[\]date= new String\[50\];

// 借出次数

int \[\]count = newint\[50\];

}

BookManager.java

package com.carlinfo.dao;

import java.text.SimpleDateFormat;

import java.util.Date;

import java.util.Scanner;

/\*\*

\* @authoryangguojun

\*

\*/

public class BookManager {

Books book = new Books\(\);

public void initial\(\) {

book.name\[0\]="Hadoop构建数据仓库实践";

book.count\[0\]=10;

book.state\[0\]=1;

book.name\[1\]="平台战略";

book.count\[1\]=20;

book.state\[1\]=0;

book.date\[1\]="2017-7-1";

book.name\[2\]="Python编程";

book.count\[2\]=10;

book.state\[2\]=1;

}

public void StartMenu\(\) {

System.out.println\("欢迎使用图书管理系统"\);

System.out.println\("-------------------------------------"\);

System.out.println\("0. 借阅排行榜"\);

System.out.println\("1. 增 加 图书"\);

System.out.println\("2. 查 看 图书"\);

System.out.println\("3. 删 除 图书"\);

System.out.println\("4. 借 书 图书"\);

System.out.println\("5. 归 还 图书"\);

System.out.println\("6. 退  出 "\);

System.out.print\("--------------------------------------\n"\);

System.out.println\("请选择"\);

Scanner input = new Scanner\(System.in\);

int choice = input.nextInt\(\);

switch\(choice\){

case 0:

list\(\);

break;

case 1:

add\(\);

break;

case 2:

search\(\);

break;

case 3:

delete\(\);

break;

case 4:

lend\(\);

break;

case 5:

returnBook\(\);

break;

case 6:

System.out.println\("\n谢谢 使 用！"\);

break;

}

}

/\*\*

\* 返回主菜单

\*/

public void returnMain\(\){

Scanner input = new Scanner\(System.in\);

System.out.print\("输入0返回："\);

if\(input.nextInt\(\) == 0\){

StartMenu\(\);

}else{

System.out.println\("输入错误, 异常终止！"\);

}

}

public void add\(\) {

System.out.println\("增加书籍"\);

Scanner input = new Scanner\(System.in\);

System.out.println\("请输入书籍名称"\);

String name = input.next\(\);

for \(int i = 0; i &lt;book.name.length; i++\) {

if\(book.name\[i\]==null\)

{

book.name\[i\]=name;

book.state\[i\]=1;

System.out.println\("图书&lt;&lt;"+book.name\[i\]+"&gt;&gt;增加成功"\);

break;

}

}

System.out.println\("\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*"\);

returnMain\(\);

}

public void list\(\) {

// 定义新数组，用来存放排序后book信息

String\[\] newname = new String\[50\]; //

int\[\] newcount = newint\[50\];

for \(int k = 0; k &lt;book.name.length; k++\) {

newname\[k\] = book.name\[k\];

newcount\[k\] = book.count\[k\];

}

// 利用冒泡排序算法进行排序

for \(int i = 0; i &lt; newname.length; i++\) {

for \(int j = i + 1; j &lt; newname.length ; j++\) {

if \(newcount\[i\] &gt; newcount\[j\]\) {

int tempc = newcount\[i\];

newcount\[i\] = newcount\[j\];

newcount\[j\] = tempc;

String tempn = newname\[i\];

newname\[i\] = newname\[j\];

newname\[j\] = tempn;

}

}

}

System.out.println\("---&gt; 排行榜\n"\);

System.out.println\("\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*"\);

System.out.println\("次数\t名称"\);

// 显示排行榜信息

for \(int i = newname.length - 1; i &gt;= 0; i--\) {

if \(newname\[i\] != null\) {

System.out.println\(newcount\[i\] + "\t&lt;&lt;" + newname\[i\] + "&gt;&gt;"\);

}

}

System.out.println\("\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*"\);

returnMain\(\);

}

public void lend\(\){

System.out.println\("---&gt; 借阅图书\n"\);

Scanner input = new Scanner\(System.in\);

System.out.print\("请输入书籍名称： "\);

String want = input.next\(\);//要借出的Book名称

for\(int i = 0; i &lt;book.name.length; i++\){

if\(book.name\[i\] == null\){//无匹配

System.out.println\("没有找到匹配信息！"\);

break;

}elseif\(book.name\[i\].equals\(want\)&&book.state\[i\]==1\){//找到匹配可借

book.state\[i\] = 0;

SimpleDateFormat format = new SimpleDateFormat\("yyyy-MM-dd hh:mm:ss"\);

String date = format.format\(new Date\(\)\);

book.date\[i\]=date;

System.out.println\("借出《"+want+"》成功!"\);

book.count\[i\]++;

break;

}elseif\(book.name\[i\].equals\(want\)&&book.state\[i\]==0\){//找到匹配已被借出

System.out.println\("《"+want+"》已被借出！"\);

break;

}

}

System.out.println\("\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*"\);

returnMain\(\);

}

publicvoid delete\(\) {

Scanner input = new Scanner\(System.in\);

boolean flag = false;// 标识删除成功与否

System.out.println\("---&gt; 删除书籍\n"\);

System.out.print\("请输入书籍名称： "\);

String name = input.next\(\);

// 遍历数组，查找匹配信息

for \(int i = 0; i &lt;book.name.length; i++\) {

// 查找到，每个元素前移一位

if \(book.name\[i\] != null&&book.name\[i\].equalsIgnoreCase\(name\)

&&book.state\[i\] == 1\) {

int j = i;

while \(book.name\[j + 1\] != null\) {

book.name\[j\] = book.name\[j + 1\];

book.state\[j\] = book.state\[j + 1\];

book.date\[j\] = book.date\[j + 1\];

j++;

}

// 最后一个不为空的元素置空

book.name\[j\] = null;

book.date\[j\] = null;

System.out.println\("删除《" + name + "》成功！"\);

flag = true;// 置位，表示删除成功

break;

} elseif \(book.name\[i\] != null

&&book.name\[i\].equalsIgnoreCase\(name\) &&book.state\[i\] == 0\) {

System.out.println\("《" + name + "》为借出状态，不能删除！"\);

flag = true;// 置位

break;

}

}

if \(!flag\) {

System.out.println\("没有找到匹配信息！"\);

}

System.out.println\("\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*"\);

returnMain\(\);

}

/\*\*

\*

\*/

publicvoid search\(\){

System.out.println\("查看图书信息"\);

System.out.println\("编号\t\t状态\t\t名称\t\t\t借阅日期"\);

for \(int i = 0; i &lt;book.name.length; i++\) {

if\(book.name\[i\]==null\)

{

break;

}

elseif\(book.state\[i\]==0\)

{

System.out.println\(\(i+1\)+"\t\t已借出"+"\t\t&lt;&lt;"+book.name\[i\]+"&gt;&gt;"+"\t\t"+book.date\[i\]\);

}

elseif\(book.state\[i\]==1\)

{

System.out.println\(\(i+1\)+"\t\t可借"+"\t\t&lt;&lt;"+book.name\[i\]+"&gt;&gt;"\);

}

}

System.out.println\("\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*"\);

returnMain\(\);

}

publicvoid returnBook\(\){

System.out.println\("---&gt; 归还书籍\n"\);

Scanner input = new Scanner\(System.in\);

longloan=0;//租金

System.out.print\("请输入书籍名称： "\);

String want = input.next\(\);

for\(int i = 0; i &lt;book.name.length; i++\){

if\(book.name\[i\] == null\){//无匹配

System.out.println\("没有找到匹配信息！"\);

break;

}elseif\(book.name\[i\].equals\(want\) &&book.state\[i\]==0\){//找到匹配

book.state\[i\] = 1;

SimpleDateFormat format = new SimpleDateFormat\("yyyy-MM-dd hh:mm:ss"\);

String date = format.format\(new Date\(\)\);

System.out.println\("\n归还《"+want+"》成功!"\);

System.out.println\("借出日期为："+book.date\[i\]\);

System.out.println\("归还日期为："+date\);

break;

}elseif\(book.name\[i\].equals\(want\) &&book.state\[i\]==1\){ //找到匹配但没有借出

System.out.println\("该书籍没有被借出！无法进行归还操作。"\);

break;

}

}

System.out.println\("\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*"\);

returnMain\(\);

}

}

Test.java

p.p1 {margin: 0.0px 0.0px 0.0px 0.0px; font: 18.0px Monaco}  
p.p2 {margin: 0.0px 0.0px 0.0px 0.0px; font: 18.0px Monaco; min-height: 25.0px}  
p.p3 {margin: 0.0px 0.0px 0.0px 0.0px; font: 18.0px Monaco; color: \#931a68}  
p.p4 {margin: 0.0px 0.0px 0.0px 0.0px; font: 18.0px Monaco; color: \#4e9072}  
span.s1 {color: \#931a68}  
span.s2 {color: \#000000}  
span.s3 {color: \#91afcb}  
span.Apple-tab-span {white-space:pre}

package com.carlinfo.dao;

public class Test {

public static void main\(String\[\] args\) {

// TODO Auto-generated method stub

BookManager bm = new BookManager\(\);

bm.initial\(\);

bm.StartMenu\(\);

}

}

