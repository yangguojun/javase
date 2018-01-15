项目实战

知识总结

卡尔信息图书管理系统

  
p.p1 {margin: 0.0px 0.0px 0.0px 0.0px; font: 18.0px Monaco}  
p.p2 {margin: 0.0px 0.0px 0.0px 0.0px; font: 18.0px Monaco; min-height: 25.0px}  
p.p3 {margin: 0.0px 0.0px 0.0px 0.0px; font: 18.0px Monaco; color: \#4f76cb}  
p.p4 {margin: 0.0px 0.0px 0.0px 0.0px; font: 18.0px Monaco; color: \#931a68}  
p.p5 {margin: 0.0px 0.0px 0.0px 0.0px; font: 18.0px Monaco; color: \#4e9072}  
span.s1 {color: \#931a68}  
span.s2 {color: \#91afcb}  
span.s3 {text-decoration: underline}  
span.s4 {color: \#000000}  
span.s5 {color: \#0326cc}  
span.Apple-tab-span {white-space:pre}  


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

