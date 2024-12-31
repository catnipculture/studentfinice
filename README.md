> #### 作者主页：[舒克日记](https://blog.csdn.net/cativen)
>
>  简介：Java领域优质创作者、Java项目、学习资料、技术互助
>
> <b><font color=red>文中获取源码</font></b>

# 项目介绍

大学生智能消费记账系统实现了字典管理、收入管理、用户管理、预算管理、支出管理、管理员管理等功能。



# 环境要求



1.运行环境：最好是java jdk1.8,我们在这个平台上运行的。其他版本理论上也可以。 

2.IDE环境：IDEA,Eclipse,Myeclipse都可以。推荐IDEA; 

3.tomcat环境：Tomcat7.x,8.X,9.x版本均可 

4.硬件环境：windows7/8/10 4G内存以上；或者Mac OS; 

5.是否Maven项目：是；查看源码目录中是否包含pom.xml;若包含，则为maven项目，否则为非maven.项目 

6.数据库：MySql5.7/8.0等版本均可；





# 技术栈



运行环境：jdk8 + tomcat9 + mysql5.7 + windows10

服务端技术：SpringBoot + MyBatis + Vue + Bootstrap + jQuery





# 使用说明





1.使用Navicat或者其它工具，在mysql中创建对应sq文件名称的数据库，并导入项目的sql文件； 

2.使用IDEA/Eclipse/MyEclipse导入项目，修改配置，运行项目； 

3.将项目中config-propertiesi配置文件中的数据库配置改为自己的配置，然后运行；





# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq 

源码地址：[http://www.codegym.top](http://www.codegym.top/)




# 运行截图

![springboot205大学生智能消费记账系统的设计与实现6](https://img-blog.csdnimg.cn/img_convert/e7f39f28fdf9e4a348534abb199f8eeb.png)

![springboot205大学生智能消费记账系统的设计与实现0](https://img-blog.csdnimg.cn/img_convert/d535718c3e46a214a15f27c387776145.png)

![springboot205大学生智能消费记账系统的设计与实现1](https://img-blog.csdnimg.cn/img_convert/7c6fa09b8b1776d87a432c8c2026669c.png)

![springboot205大学生智能消费记账系统的设计与实现2](https://img-blog.csdnimg.cn/img_convert/f28634744267070e9505dcd5fd4e1416.png)

![springboot205大学生智能消费记账系统的设计与实现3](https://img-blog.csdnimg.cn/img_convert/23471b65c856789e99363502b62b49a9.png)

![springboot205大学生智能消费记账系统的设计与实现4](https://img-blog.csdnimg.cn/img_convert/c361d904680808011ffbf1cdeb6adb49.png)

![springboot205大学生智能消费记账系统的设计与实现5](https://img-blog.csdnimg.cn/img_convert/d4a9c7e0a9cb377e99810f34ea6be2be.png)





```java
	public String generateToken(Long userid,String username, String tableName, String role) {
		TokenEntity tokenEntity = this.selectOne(new EntityWrapper<TokenEntity>().eq("userid", userid).eq("role", role));
		String token = CommonUtil.getRandomString(32);
		Calendar cal = Calendar.getInstance();   
    	cal.setTime(new Date());   
    	cal.add(Calendar.HOUR_OF_DAY, 1);
		if(tokenEntity!=null) {
			tokenEntity.setToken(token);
			tokenEntity.setExpiratedtime(cal.getTime());
			this.updateById(tokenEntity);
		} else {
			this.insert(new TokenEntity(userid,username, tableName, role, token, cal.getTime()));
		}
		return token;
	}

```
